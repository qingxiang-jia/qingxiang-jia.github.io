---
layout: post
title: Sentence Screen Fitting
tags:
- Algorithm

---

You are given a sentence (a list of words (strings)) and the dimension of the screen (given by rows x cols) [(full LeetCode description)](https://leetcode.com/problems/sentence-screen-fitting/). Compute how many times the full sentences can be printed onto the screen. Between sentences, there should be a space except that the last sentence ends at the end of last row. Between words, there should be a space except that the last word ends at the end of last row. A word cannot be broken into two rows.

Naively, we can just fill the screen as we go, but it turns out to be unacceptable for the OJ. So we need to find something more clever. If we think of what we are filling as an infinite sequence with characters (and spaces) just like how Turing machines work with the infinite sequence, we only need to know where we finally stop on the sequence, and divide the number by the length of a "unit sequence".

Now, what is a "unit sequence". By that I just mean a formatted sentence, so we don't have to think about inserting a space between words and sentences. For example, if we have the sentence as ["what", "a", "stupid", "question"]. The unit sequence is "what\_a\_stupid\_question\_" where "\_" represents space.

The algorithm then seems to be quite simple since all we do is increment cols for each row, and then divide it by the length of the unit sequence. However, there are two edge cases we need to take care of.

Before we talk about the algorithm, let's define cursor as the position (with respect to the infinite sequence) of the last character (can be a space) filled in the screen + 1. So, alternatively, cursor is just the start position (with respect to the infinite sequence) of the first row that cannot be displayed on the screen.

The first case is that when cursor points to a space. This means, either we are starting a new word, or we are starting a new sentence. Either way, that space shouldn't be there (recall that the space is only inserted between words and sentences). Because we are at the first position of a new row, we don't need a space to separate two words or two sentences. So we increment cursor by one to skip that space. There is a [post](https://discuss.leetcode.com/topic/62455/21ms-18-lines-java-solution) explains this case with more details (bottom of that post).

The second case is that when neither the cursor is pointing at a space nor the (cursor - 1) is. What is this situation? Well, recall that the infinite sequence comes with a space between words (and sentences), if both infinite_sequence[cursor] and infinite_sequence[cursor - 1] points to non-space characters, that means the word is broken into two rows. This is prohibited by the requirements. So, we should back up until cursor points to a non-space character, and (cursor - 1) points to a space.

The following is my Java solution:

```
public int wordsTyping(String[] sentence, int rows, int cols) {
    String sequence = String.join(" ", sentence) + " ";
    int cursor = 0;
    for (int row = 0; row < rows; row++) {
      cursor += cols;
      if (sequence.charAt(cursor % sequence.length()) == ' ') {
        cursor++; // first case
      } else {
        while (cursor > 0 && sequence.charAt((cursor - 1) % sequence.length()) != ' ') {
          cursor--; // second case
        }
      }
    }
    return cursor / sequence.length();
}
```