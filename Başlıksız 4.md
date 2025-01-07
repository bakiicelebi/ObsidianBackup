package Task1;

  

import java.util.regex.Matcher;

import java.util.regex.Pattern;

  

public class CounterJDoc implements ICounter {

    private String regex = "/\\*\\*.*?\\*/";

  

    @Override

    public int count(String source) {

        Pattern pattern = Pattern.compile(regex, Pattern.DOTALL);

        Matcher matcher = pattern.matcher(source);

  

        int javadocLineCount = 0;

        while (matcher.find()) {

            String javadoc = matcher.group();

            String[] lines = javadoc.split("\r\n|\r|\n");

  

            javadocLineCount += lines.length - 2;

        }

        return javadocLineCount;

    }

  

}