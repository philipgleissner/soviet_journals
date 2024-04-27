# Soviet Journals Reconnected (SJR) | Documentation

This is the data repository of the digital humanities project Soviet Journals Reconnected (SJR), which was developed during a year-long graduate fellowship at the Princeton Center for Digital Humanities in 2016/2017. With the help of several quantitative approaches, especially social network analysis, the analysis of this data provided the foundation for a chapter in the book _Subscribing to Sovietdom: The Lives of the Socialist Literary Journal_ (forthcoming with University of Toronto Press), the article "‘Somehow, I Wasn’t Drawn into the Editorial Office of Novyi Mir’: Digital Approaches to the Literary Environment of Late Socialist Journals." (Russian Literature 122-123, 2021), and a number of conference presentations. This document provides contextual commentary and an overview of the data, which are publicly accessible for scholarly use.

**Provenance of Data**

The data of SJR dataset were developed on the basis of the Soviet index of the periodical press, the so-called _Chronicle_ of Journal Articles (Letopis’ zhurnal’nykh statei). For the time period of 1958-1972, this index has been digitized by Indiana University and was available as a research aid online until 2021. The raw data of this digitized index included bibliographical entries for all contributions published in Soviet periodicals as an unencoded string of text. In SJR, these data transcend their function as research aid and become an object of research and analysis in their own right. 

**Data Processing**

In preparation for scholarly analysis and interpretation, the data were **parsed**. This means that each entry in the bibliographical list was divided into several data fields, a process that in many cases could rely on the use of regular expression and the data cleaning tool Open Refine. At the same time, the data were reviewed repeatedly, to correct errors that occured in the parsing process. 

In a second step, the data were **normalized**. 

This involved **unifying the spelling** of individual journal titles that were used interchangeably by the Soviet bibliographers, e.g. _Иностранная литература_ vs _Иностр. литература_, both of which refer to the journal _Inostrannaia literatura_. 

All titles, author names, journal titles were also transliterated, following the Library of Congress system for Cyrillic Russian transliteration (without diacritics and ligatures, which tend to interfere with tools for computational analysis). Some of this transliteration was done by hand or with the help of regular expressions in a plain text editor. At a later stage, I relied on the data cleaning tool Open Refine, and I provide a brief tutorial on automatic transliteration on my research blog at https://philipgleissner.com/automatic-transliteration-using-open-refine/.

The final and most complicated step was **author attribution**. Every individual author in this dataset needed to be an identifiable unit in order to provide consistent reference--and to allow for usage of the data in social network analysis, which relies on the notion of identifiable individuals. In contrast, the digitized _Chronicle_ featured authors in whichever way they appeared in the journals—with or without patronymic, with first initials only, and, in the case of foreign authors, in changing transliteration. Author names also appear to be the most common realm of typos in the generally very meticulous index. An advantage for the project is that anonymous publication and the use of changing pseudonyms were rather rare within the system of official literature—unlike among samizdat and tamizdat authors. 

Soviet Journals Reconnected follows the internationally agreed library standard of the **Virtual International Authority File (short: VIAF**), where each author featured has a unique ID. For example, Lev Nikolaevich Tolstoi's ID is 96987389, which it can serve as a good example here. This unique identifier connects all National Libraries' spellings (Лев, Lev, Lew, Leo, Leon, Толстой, Tolstoi, Tolstoy, Tolstoi). Adding the VIAF ID for every author in this dataset allowed me to add consistently attribute authorship of the individual contributions indexed--without going back and actually changing the author names in the original data, making thus transparent the editorial decisions and, at times, ambivalence of the data. 

This process involved many editorial decisions. Much of the reconciliation of author names and VIAF IDs was undertaken, again, with the use of Open Refine, but it needed to be carefully reviewed. Whereas many cases of author identities are obvious, e.g. Aleksandr Solzhenitsyn (95215697), there are numerous less famous writers with common names where identities needed to be established. For a number of authors, no VIAF IDs were available at all. In many cases, these were barely known individuals who often only come up once in the complete dataset and are therefore negligible for network analysis that focuses on repeat publications. These authors without VIAF IDs were assigned alternative IDs, commonly starting with the letter A.

**Data Format**

The project Soviet Journals Reconnected consists exclusively of plain text data, organized in columns in tab-separated (TSV) text files. For the user, these ultimately appear as spreadsheets. They can be viewed either in plain text editors or in commonly used spreadsheet programs (Microsoft Excel, Numbers, Google Sheets). Originally, the data of this project were in a MySQL relational database, which in practice proved to be too hard to maintain for an individual researcher and limited access for others. Plain text spreadsheets, on the other hand, have the advantage that they are long-lived, less prone to damage, and intuitively understandable to scholars with and without digital humanities training. They can provide the foundation for further computational analysis, but also have the affordance of a reference or research aid when accessed through a basic full text search.

**Use and Citation**

This bibliographical data is not subject to copyright and researchers are welcome to use it in whichever way they would like. Since significant labor went into processing this data, I would, however, be grateful for a citation in the form of a reference to the projects primary article publication: 

Philip Gleissner, “‘Somehow, I Wasn’t Drawn into the Editorial Office of Novyi Mir’: Digital Approaches to the Literary Environment of Late Socialist Journals.” _Russian Literature_ 122-123 (2021): 163-191.

While the Indiana University Library's digital _Letopis'_ is not being maintained anymore and has been made inaccessible to the public, I believe that a reference to the following publication can serve to acknowledge its foundational contribution:

Murlin Croucher, “Digitizing and Making a Web Site for the Soviet Letopis’ Zhurnal’nykh Statei, 1956-1975,” _Slavic & East European Information Resources_ 3, no. 2/3 (2002): 179-183. 

**Available Data in this Repository**

The data provided here follow the underlying notion there there is no such thing as a perfect and finished dataset but rather iterations of revised ones that come ever closer to an ideal state and respond to a variety of research uses. This is reflected in the various versions of the dataset provided in this repository, which are sporadically updated or augmented. The following descriptions are designed to help the researcher identify which versions of the dataset they may find most helpful for their use. 

**The repository contains the following datasets in Two Categories: Supplementary Data and Core Data**

_Supplementary Data_

This part of the dataset is, in fact, not extracted from the digitized _Letopis'_ but rather collected from front and back matter of the individual journals. In the scholarly publications associated with this project, these data used to make a broader argument about the literary sociology of Soviet journals.

_Circulation by Journal, Issue, Year (circulation.tsv)_

This tab separated values (tsv) file lists the print run (i.e. number of copies printed) for each issue of the six journals (_Znamia_, _Molodaia gvardiia_, _Nash sovremennik_, _Novyi  mir_, _Oktiabr'_, _Iunost'_) for the time period 1958-1972. It features the columns 'journal' (journal title), 'issue' (issue number, out of 1-12 or 1-6), 'year' (year of the issue), 'print_run' (circulation of the journal according to information given in the back matter of the journal issue), 'issues_pa' (number of issues published during the given year - 12 = monthly, 6 = bimonthly), 'notes' (notes on how information was captured).

_Editors Lists (e.g. editors_molodaia_gvardiia.tsv, editors_iunost.tsv, etc.)_

This file lists the members of the editorial teams of the respective journals by year and issue number. These lists are compiled according to information given in the back matter of the journal issues. Chief editor (главный редактор), deputy editor (заместитель главного редактора), and managing editor (отсветственный секретарь) are commonly listed separately, which is reflected in this file. The remaining editors are listed in alphabetical order, not indicative of their actual involvment and field of responsibilities in the journal, which would need to be established on a case-by-case basis and is analyzed in the book _Subscribing to Sovietdom_ through the lens of memoir literature and archival documents.

_Core Data_

The core data section consists of the foundational data of this project: the bibliographical entries of the Soviet Chronicle of Journal Articles, digitized by Indiana University. Within this section, the data are provided at various stages of parsing, cleaning, and normalization, and are divided into different subsets, which can be chosen by the researcher based on their individual needs. Many further sub-sets of the data can be imagined, but a few suggestions are included (e.g. filtered by genre) to highlight further potential research uses.

_Basic Parsed Data by Journals (e.g. basic_oktiabr.tsv, basic_nash_sovremennik.tsv., etc.)_

Data in a minimally processed format. Parsed into the following columns: 'aut_lastn, aut_firstn' (authors as they appear in the Chronicle; repeated twice to accommodate cases where there are up to three multiple authors), contribution_title (titles as they appear in chronicle, including genre denominators), 'journal' (journal title), 'year' (year of issue),	'issue (issue number, out of 1-12 or 1-6),	'page_range' (start and end page, divided by dash). Individual files for each journal. In _Subscribing to Sovietdom_ the individual journals' datasets were used to establish and compare the frequency of keywords in the contribution titles of the publications.

_The Complete Data, Parsed, Featuring VIAF IDs, and Transliterations_

This tsv file of 10,590 lines offers the complete SJR dataset. It is parsed into the following data fields: 'contribution_title' (contribution title in Russian), aut_id (the author's ID as assigned for the use of this dataset. If the author has a VIAF ID, this is used. If the author is not catalogued in the VIAF, a unique ID was created for the use of this project),	'aut_viaf' (the authors VIAF ID, if available), 'aut_lastn_r' (the author's last name in Russian),	'aut_firstn_r'  (the author's first name in Russian),	'aut_lastn_e' (the author's last name, transliterated into the Latin alphabet),	 aut_firstn_e (the author's first name, transliterated into the Latin alphabet), 'journal' (title of the journal),	'year' (year of publication),	'issue' (issue number of publication),	'start_page' (first page of contribution),	end_page (last page of contribution),	'pagetotal' (total number of pages of the contribution).

