---
layout: post
title: Convert Plaintext to ANKI Decks
tags:
- Java

---
[ANKI](http://ankisrs.net/) is a software that uses flash cards to help you memorize stuff, such as improving vocabulary for a foreign languge. I have a vocabulary book in `.doc` format, and I want to convert it into decks of flash cards that Anki can recongnize.

After some massage, I obtained a text file with the following layout:

```
word
definition1
definition2

word
definition1

word
definition1
definition2
definition3
```

Anki accepts [several plaintext formats](http://ankisrs.net/docs/manual.html#importing), the one I used, is:

```
hello; this is<br>a two line answer
two; this is a one line one
```

where as you can see, `<br>` denotes a line break. Then I wrote the following code to convert it to Anki-friendly text file, and imported to Anki. Code itself is trivial (also quite and dirty), but it's fine for this type of one-time task.

```
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.PrintWriter;
import java.util.ArrayList;

public class Txt2AnkiDeck {
  public static void main(String[] args) throws Exception {
    ArrayList<ArrayList<String>> entries = new ArrayList<>();
    String filename = "21.txt";
    try (BufferedReader br = new BufferedReader(new FileReader(filename))) {
      String line;
      ArrayList<String> entry = null;
      while ((line = br.readLine()) != null) {
        if (line.length() == 0) {
          entries.add(entry);
          entry = null;
        } else {
          if (entry != null) {
            entry.add(line);
          } else {
            entry = new ArrayList<>();
            entry.add(line);
          }
        }
      }
      // verify it works, yes
      for (ArrayList<String> singleEntry : entries) {
        for (String l : singleEntry) {
          System.out.println(l);
        }
        System.out.println();
      }
      // output decks to file
      PrintWriter writer = new PrintWriter(filename + "-o.txt", "UTF-8");
      for (ArrayList<String> deck : entries) {
        for (int i = 0; i < deck.size(); i++) {
          if (i == 0) { // is word
            writer.print(deck.get(i) + "; ");
          } else { // is definition
            writer.print("<br>" + deck.get(i));
          }
        }
        writer.println("");
      }
      writer.close();
    }
  }
}
```