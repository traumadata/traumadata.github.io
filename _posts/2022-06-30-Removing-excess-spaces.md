---
author: Jake Roden-Foreman
date: 2022-06-30
editor_options:
  chunk_output_type: console
excerpt: Trauma registry export files are the one scenario where I don’t
  want extra space(s).
knit: "(function(inputFile, encoding) { rmarkdown::render(inputFile,
  encoding = encoding, output_dir = “../\\_posts”) })"
output:
  md_document:
    preserve_yaml: yes
    variant: gfm
tags:
- Trauma
- Report Writing
- Data
title: Removing excess spaces
toc: true
---



<img src="/img/posts/2022-06-30-Removing-excess-spaces/excess_spaces_pre_post.png" alt="A screenshot showing the file sizes of the report files before and after removing excess spaces" width="80%">

# The problem

Anyone who has worked with trauma registry data has probably noticed
that when you open a data export file there are a lot of excess spaces,
and I do mean *a lot*. TraumaBase by CDM has a feature to trim the
excess spaces from reports, but it isn’t on by default, and you have to
specify that feature for each variable in the export. I haven’t seen
similar features in other registry programs.

Most people don’t seem to be bothered by these excess spaces, but I know
a handful of people are (myself included). For one, I think they make
the exports a bit messy. When I’m briefly looking over the data, I like
to use Ctrl + arrow key to jump to the next non-empty cell. As an
example, that keyboard shortcut lets me quickly jump past numerous empty
placeholder columns for procedures and get to the next set of variables.

The other main issue I have with the excess spaces is that they make the
data files *soooo* much bigger than they need to be. It’s not
infrequently that I see files that are 90% smaller after removing excess
spaces. That’s 90% of a file being used to hold absolutely no
information! That’s crazy to me.

# The solution

The standard way for people to get rid of excess spaces is to use the
find and replace feature in Excel. That will definitely do the job, but
it can be painfully slow. So, I made a little macro to speed things up a
bit.

# The test

To compare how long it takes to remove excess spaces using the standard
find and replace versus using my macro, I wanted a realistic test. So, I
made a report with some variables that would be included in just about
any research project: trauma registry ID number, ICD-10 procedure codes,
and ICD-10 diagnosis codes. The report includes 1,265 rows (one per
patient) and 251 columns (trauma ID, 200 procedures, and 50 diagnoses).

When I ran the comparisons with the file as a CSV file, both methods
decreased the file size from 4,565 KB to 442 KB, but my macro was about
four times faster than using find and replace (39 seconds vs. 9
seconds).

Results were nearly identical when I saved the report file as XLSX file:
both methods decreased the file size from 1,048 KB to 125 KB, but my
macro was roughly four times faster than find and replace (41 seconds
vs. 10 seconds).

Notably, both of the macro times include about 3 seconds to select the
report file.

You can <a href="/assets/Remove excess spaces.xlsm">download the file to
run the macro here</a>.

  
  

I really do hope this tool will be helpful, but if you run into issues
with it or have questions, send me an
[email](mailto:TraumaDataBlog@gmail.com) or leave a comment below. I’d
also love suggestions for future topics.

To see the code I used to create this post, [click
here](https://github.com/traumadata/traumadata.github.io/blob/master/_source/2022-06-30-Removing-excess-spaces.Rmd).
