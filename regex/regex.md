* character class [ ]
    * matches only one out of several characters
    * eg. find identifier in a programming language
        * [A-Za-z_][A-Za-z_0-9]*
        
         ![Explanation](https://ibb.co/eAtTR8)



* negated character class [^ ]
    * matches only one of the characters that is not presented between []

* repeat a character class by using ? , * or +
* repeat the matched character set ([0-9])\1+
    * () are used to capture the group
    * \1 matches the results of capture group 1
  