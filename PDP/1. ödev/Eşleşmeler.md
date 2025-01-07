

**REGEX


**numarada eşleşme sayısı

![[Pasted image 20240330215832.png]]

![[Pasted image 20240330215944.png]]


**stringte eşleşme değiştirme

![[Pasted image 20240330220422.png]]

![[Pasted image 20240330220438.png]]



**Asal Sayı Kontrolü**

![[Pasted image 20240330221038.png]]



Javadoc dosyalarını taramak için bir regex düzenlemesi oluşturabiliriz. Javadoc genellikle `/**` ile başlayıp `*/` ile biten çok satırlı yorumlar olarak yazılır. İşte bu tür bir çok satırlı yorumları bulmak için bir Java regex örneği:

```java
String regex = "/\\*\\*.*?\\*/";
```

Bu regex deseni aşağıdaki parçalardan oluşur:

- `/\*\*`: `/**` karakter dizisini eşleştirir.
- `.*?`: Herhangi bir karakteri sıfır veya daha fazla kez eşleştirir (`*`), ancak mümkün olduğunca az sayıda eşleşme yapar (`?`).
- `\*/`: `*/` karakter dizisini eşleştirir.

Bu regex, çok satırlı yorumları baştan sona kadar eşleştirecektir. Ancak, içeride başka çok satırlı yorumlar olup olmadığını kontrol etmeyecek, yani iç içe geçmiş çok satırlı yorumları düzgün bir şekilde ele almayacaktır. İç içe geçmiş yorumları da ele almak istiyorsanız daha karmaşık bir regex kullanmanız gerekebilir.

Bir Javadoc dosyasındaki çok satırlı yorumları taramak için bu regex'i kullanabilir ve Java'da `Pattern` ve `Matcher` sınıflarını kullanarak uygulayabilirsiniz. Örneğin:

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class JavadocScanner {
    public static void main(String[] args) {
        String javadoc = "Your Javadoc content here /** Javadoc comment */ Some code /* Another comment */ More code /** Another Javadoc comment */";
        String regex = "/\\*\\*.*?\\*/";
        
        Pattern pattern = Pattern.compile(regex, Pattern.DOTALL);
        Matcher matcher = pattern.matcher(javadoc);
        
        while (matcher.find()) {
            System.out.println(matcher.group());
        }
    }
}
```

Bu kod, verilen bir metin içindeki tüm Javadoc yorumlarını ekrana yazdıracaktır.