``` tsx
import { useEffect, useState } from "react";

import RNFS from "react-native-fs";

import AsyncStorage from "@react-native-async-storage/async-storage";

  

const LOGS_DIR = `${RNFS.DocumentDirectoryPath}/logs`;

const BUFFER_SIZE = 10;

const LOG_RETENTION_DAYS = 7;

const ERROR_LOG_KEY = "server_errors";

  

// Log buffer to store logs temporarily

let logBuffer: string[] = [];

let currentLogFile = "";

  

// Definition of log types

type LogType =

  | "INFO"

  | "WARN"

  | "ERROR"

  | "BLUETOOTH_INFO"

  | "BLUETOOTH_ERROR"

  | "SERVICE_ERROR"

  | "CONNECTED_TO_SERVER"

  | "DISCONNECTED_TO_SERVER"

  | "RECONNECTED_TO_SERVER";

  

// Function to update the log file (globally stored)

const updateLogFile = () => {

  const fileName = `logs_${new Date().toISOString().replace(/:/g, "-").slice(0, 13)}.txt`;

  currentLogFile = `${LOGS_DIR}/${fileName}`;

};

  

// Function to write logs to the file

const flushLogs = async () => {

  if (logBuffer.length === 0) return;

  

  const logsToWrite = logBuffer.join("\n") + "\n";

  logBuffer = []; // Reset the buffer

  

  console.log("Attempting write logs in buffer")

  

  try {

    await RNFS.mkdir(LOGS_DIR);

    await RNFS.appendFile(currentLogFile, logsToWrite, "utf8");

    console.log("Writing is successfull")

  } catch (error) {

    console.log("Error writing logs:", error);

  }

};

  

// Function to delete old logs

const deleteOldLogs = async () => {

  try {

    const files = await RNFS.readDir(LOGS_DIR);

    const now = Date.now();

  

    for (const file of files) {

      const fileInfo = await RNFS.stat(file.path);

      const fileAge = now - new Date(fileInfo.mtime).getTime();

  

      if (fileAge > LOG_RETENTION_DAYS * 24 * 60 * 60 * 1000) {

        await RNFS.unlink(file.path);

      }

    }

  } catch (error) {

    console.log("Error deleting old logs:", error);

  }

};

  

export const useLog = () => {

  const [_, setForceUpdate] = useState(0); // Trigger hook update when buffer changes

  

  // Set up log file when the hook is first called

  useEffect(() => {

    if (!currentLogFile) updateLogFile();

  

    const interval = setInterval(flushLogs, 60 * 60 * 1000); // Update log file every hour

    return () => clearInterval(interval);

  }, []);

  
  

  // Function to add a log entry

  const addLog = (type: LogType, message: string) => {

    const logEntry = `[${new Date().toISOString()}] [${type}] ${message}`;

    console.log(logEntry);

  

    logBuffer.push(logEntry); // Add logs to central buffer

    setForceUpdate(prev => prev + 1); // Update the hook

  

    if (logBuffer.length >= BUFFER_SIZE) flushLogs();

  

    if (

      type === "CONNECTED_TO_SERVER" ||

      type === "DISCONNECTED_TO_SERVER" ||

      type === "BLUETOOTH_ERROR" ||

      type === "BLUETOOTH_INFO" ||

      type === "SERVICE_ERROR" ||

      type === "ERROR"

  

    ) {

      saveServerError({ action: type, description: logEntry });

    }

  };

  

  // Function to save server errors locally

  const saveServerError = async (data: any) => {

  

    //AsyncStorage.removeItem(ERROR_LOG_KEY)

  

    try {

      const existingLogs = await AsyncStorage.getItem(ERROR_LOG_KEY);

      const logsArray = existingLogs ? JSON.parse(existingLogs) : [];

      logsArray.push(data);

      await AsyncStorage.setItem(ERROR_LOG_KEY, JSON.stringify(logsArray));

    } catch (error) {

      console.log("Failed to save server error log locally:", error);

    }

  };

  

  // Function to retrieve server errors

  const getServerErrors = async () => {

    try {

      const res = await AsyncStorage.getItem(ERROR_LOG_KEY);

      return res ? JSON.parse(res) : [];

    } catch (error) {

      console.log("Failed to get server error log from local:", error);

      return [];

    }

  };

  

  // Function to remove a specific server error

  const removeServerErrorStorage = async (log: any) => {

    try {

      const existingLogs = await AsyncStorage.getItem(ERROR_LOG_KEY);

      const logsArray = existingLogs ? JSON.parse(existingLogs) : [];

  

      const updatedLogs = logsArray.filter((storedLog: any) => storedLog.description !== log.description);

      await AsyncStorage.setItem(ERROR_LOG_KEY, JSON.stringify(updatedLogs));

    } catch (error) {

      console.log("Failed to remove server error log from local:", error);

    }

  };

  

  // Function to list log files

  const getLogFiles = async (): Promise<string[]> => {

    try {

      const files = await RNFS.readDir(LOGS_DIR);

      return files.map(file => file.name);

    } catch (error) {

      addLog("ERROR", "Error reading log directory, error message: " + error);

      return [];

    }

  };

  

  // Function to read a specific log file

  const readLogFile = async (fileName: string): Promise<string> => {

    try {

      const filePath = `${LOGS_DIR}/${fileName}`;

      return await RNFS.readFile(filePath, "utf8");

    } catch (error) {

      addLog("ERROR", "Error reading log file, error message: " + error);

      return "Error reading log file.";

    }

  };

  

  // Clean up old logs (once per day)

  useEffect(() => {

    const interval = setInterval(deleteOldLogs, 24 * 60 * 60 * 1000);

    return () => clearInterval(interval);

  }, []);

  

  return {

    addLog,

    getLogFiles,

    readLogFile,

    getServerErrors,

    removeServerErrorStorage,

  };

};
```

