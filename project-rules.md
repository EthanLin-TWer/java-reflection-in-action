### Updated time: 02:29:33 10 Aug, 2015.

 1. #### Definitions  
 All definitions used in this .md file are restricted to this translation project and are defined to help to clarify concepts or entities we're going to talk about in the following writing.
  * A Paragraph: Either a Chinese translated paragraph or an English original paragraph which doesn't have any new-line characters. 
  * A Block: A translated paragraph and its corresponding paragraph together are combined as a block.
 2. #### Headers
  * Chapter headers(i.e. files in /chapter_?/0-xxx.md) are sized to header1.
  * Section headers are sized to header2.
  * Sub-section headers are sized to header3.
 3. #### Contents
  * A soft break is used between a translated paragraph and its' corresponding original text paragraph.
  * A hard break is used between a original & translated block and another.
  * 3 blank lines are used to separate two different blocks in .md files, although it makes no difference in Gitbook's representation page whether one or two or three blank lines are used to distinguish different blocks.
 4. #### Displayed titles in Gitbook
  * The Chinese translation is used to display a chapter/section's title.
  * While displayed in the previous way, the English title of the corresponding chapter/section is instead used in the source file(the markdown file)'s name.
  * With all displayed titles initialized to English version in the source files, they can simply be changed into Chinese ones in the root SUMMARY.md file without breaking the existing relative link to the origin files in the source directory. All you need is just rerun the 'gitbook init' command line.

### 2015年8月10日 02:29:33更新

 1. #### 定义
 本.md文件所用的所有定义作用范围均为本翻译项目，目的在于更明确地澄清接下来写作过程中出现的一些概念和实体的定义。  
  * Paragraph(自然段/段落）。一个自然段指的是一个原文（英语）或译文（中文）的段落。
  * Block(区块）。一个区块指的是由一个英文原文段落与其对应的中文译文段落组成的一个整体。

 2. #### 章/节标题  
  * 章标题使用header1样式。
  * 节标题使用header2样式。
  * 节下的小节使用header3样式。

 3. #### 内容  
  * 译文段落与原文段落使用软换行方式分隔。
  * 区块之间使用硬换行方式分隔。
  * 在.md源文件中，区块之间采用3个空行来分隔。尽管就Gitbook页面上的显示效果而言，使用多少个空行并没有影响，但3个空行使源文件中区块之间分隔比较明显。

 4. #### Gitbook目录展示的标题  
  * 章/节目录的标题使用中文，由原文标题翻译过来。
  * 但对应的源文件依然使用其原文标题来命名。
  * 使用SUMMARY建立目录时，源文件夹下的文件初始都是赋以英文的原文标题，但它们可以在SUMMARY.md文件中更改，并且不会影响现有的中文标题与源文件间的连接关系。更改目录标题为中文后只需要运行'gitbook init'命令即可。