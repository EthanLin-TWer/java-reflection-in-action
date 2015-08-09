### Updated time: 02:29:33 10 Aug, 2015.
 1. Definitions
 All definitions used in this .md are restricted to this translation project and are defined to help clafifying concepts or entities we're going to talk about in the following writing.
  * Paragraph: Either a Chinese translated nature paragraph or a English original text nature paragraph here in where a 'nature paragraph', is defined as a block of text combined with sentences or/and words and in the mean time a way we, human beings, instead of a computer or other electronic devices, use to communicate, write or express.
  * Block: A translated paragraph and its' corresponding paragraph together are combined as a block.
 2. Headers
  * Chapter headers(i.e. files in /chapter_?/0-xxx.md) are sized to header1.
  * Section headers are sized to header2.
  * Sub-section headers are sized to header3.
 3. Contents
  * A soft break is used between a translated paragraph and its' corresponding original text paragraph.
  * A hard break is used between a original&translated block and another.
  * 3 blank lines are used to separate two different blocks in .md files, although it makes no difference in Gitbook's representation page whether one or two or three blank line(s) is(are) used to distinguish different blocks.
 4. Displayed titles in Gitbook
  * The Chinese translation is used to display a chapter/section's title.
  * While displayed in the previous way, the English title of the corresponding chapter/section is instead used in the source file(the markdown file)'s name.
  * With all displayed titles initialized to English version in the source files, they can simply be changed into Chinese ones in the root SUMMARY.md file without breaking the existing relative link to the origin files in the source directory. All you need is just rerun the 'gitbook init' command line.