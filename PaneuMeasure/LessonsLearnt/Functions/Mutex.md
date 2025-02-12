``` javascript
// Function to add a log entry

  const addLog = async (type: LogType, message: string) => {

    const date = new Date();

  

    const formattedDate = date.toLocaleString('tr-TR', {

      day: '2-digit',

      month: '2-digit',

      year: 'numeric',

      hour: '2-digit',

      minute: '2-digit',

      second: '2-digit',

      hour12: false, // 24h format

    });

  

    // Generate a precise ID using timestamp + random number

    const logId = `${Date.now()}${Math.floor(Math.random() * 100000)}`;

    console.log(`[${formattedDate}] [${type}] ${message}`);

    setForceUpdate(prev => prev + 1); // Update the hook

  

    await saveLogs({

      id: logId,

      action: type,

      description: message,

      pdaDate: dateToISOLikeButLocal(date),

    });

  };

  

  // Function to save server errors locally

  const saveLogs = async (data: any) => {

    while (isSaving) {

      // it is for waiting if any log is being saved

      await new Promise(resolve => setTimeout(resolve, 10));

    }

  

    isSaving = true;

    try {

      const existingLogs = await AsyncStorage.getItem(LOG_KEY);

      const logsArray = existingLogs ? JSON.parse(existingLogs) : [];

      logsArray.push(data);

      await AsyncStorage.setItem(LOG_KEY, JSON.stringify(logsArray));

    } catch (error) {

      console.log(`Failed to save ${LOG_KEY} log locally: `, error);

    } finally {

      isSaving = false;

    }

  };
```
