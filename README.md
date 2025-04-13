# CBT816
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 816 is from Sam Golob and contains an APF-authorized      *   FILE 816
//*           TSO command to quickly and instantly change the       *   FILE 816
//*           default number of Global Notices that an ACCOUNT      *   FILE 816
//*           and SYNC combination will create, when it formats     *   FILE 816
//*           a SYS1.BRODCAST dataset (or any active Broadcast      *   FILE 816
//*           Dataset).                                             *   FILE 816
//*                                                                 *   FILE 816
//*           The IBM default value is 100 lines of notices. This   *   FILE 816
//*           is adequate for most shops, but if you need to        *   FILE 816
//*           change it, it is a large "pain in the neck" to do     *   FILE 816
//*           it IBM's way.  To do it our way, it is easy, and      *   FILE 816
//*           it takes a small fraction of a minute, with no IPL.   *   FILE 816
//*           Just execute one (APF-authorized) TSO command.        *   FILE 816
//*                                                                 *   FILE 816
//*           email:  sbgolob@cbttape.org                           *   FILE 816
//*                                                                 *   FILE 816
//*           IBM officially makes this number very difficult       *   FILE 816
//*           to change.  You have to zap the hex number into       *   FILE 816
//*           csect IKJEBLMT of module IKJEFXSR and the change      *   FILE 816
//*           will not take effect until the next IPL.  Very        *   FILE 816
//*           silly and unlike IBM....  They must have had a        *   FILE 816
//*           reason when it was designed, but it doesn't seem      *   FILE 816
//*           to make much sense nowadays, with IPLs so few         *   FILE 816
//*           and far between.                                      *   FILE 816
//*                                                                 *   FILE 816
//*           Fortunately, there is a solution.  The actual         *   FILE 816
//*           number that SYNC looks at, is located squarely        *   FILE 816
//*           in the CVT itself.  It isn't even chained off it!     *   FILE 816
//*           The number is a fullword at location CVT + X'5A8'.    *   FILE 816
//*           And loading this up initially, is the reason for      *   FILE 816
//*           the necessity of an IPL.                              *   FILE 816
//*                                                                 *   FILE 816
//*           IBM could have done better (and it still might,       *   FILE 816
//*           if you submit a requirement for a console command     *   FILE 816
//*           to change the default, through SHARE).  However,      *   FILE 816
//*           we are not waiting for IBM.  Here is a TSO command    *   FILE 816
//*           (that of course has to be APF-authorized), which      *   FILE 816
//*           will change the number instantly in the CVT, by       *   FILE 816
//*           simply plugging in a new number.  It works.  Just     *   FILE 816
//*           say BDMNNOTC 500, and an ACCOUNT + SYNC will produce  *   FILE 816
//*           a Broadcast Dataset that has 500 Global Notices       *   FILE 816
//*           messages.  Set a different number, and you get        *   FILE 816
//*           that number of Global Notices produced by the         *   FILE 816
//*           ACCOUNT + SYNC.  In my experience, you can even       *   FILE 816
//*           go over 1000 (IBM's professed limit).  I created      *   FILE 816
//*           a Broadcast Dataset with 4000 Notice slots, and       *   FILE 816
//*           it appears to work just fine.                         *   FILE 816
//*                                                                 *   FILE 816
//*           Again, you have to APF-authorize this TSO command     *   FILE 816
//*           by including its name in table IKJEFTE2 (authcmd)     *   FILE 816
//*           in PARMLIB, or by using one of our tools (TSUB,       *   FILE 816
//*           LWATMGR, or LLWA) that are in CBT Files 185 and       *   FILE 816
//*           797.  Good luck.                                      *   FILE 816
//*                                                                 *   FILE 816
//*           Note:  I have not imposed an upper limit on the       *   FILE 816
//*           number CVTBCLMT within the BDMNNOTC program.  But     *   FILE 816
//*           my advice is that it shouldn't be over 1000 in        *   FILE 816
//*           a production environment.  (SBG - 12/2009)            *   FILE 816
//*           With large numbers, errors caused by ACCOUNT +        *   FILE 816
//*           SYNC might occur.                                     *   FILE 816
//*                                                                 *   FILE 816
//*           I am supplying a load module library in member        *   FILE 816
//*           LOADMODS, which contains my commercial BDMCLEAN       *   FILE 816
//*           program as well as BDMNNOTC.  BDMCLEAN is a TSO       *   FILE 816
//*           command that cleans up deleted junk in Broadcast      *   FILE 816
//*           Datasets that makes them hard to browse or REVIEW.    *   FILE 816
//*           (REVIEW is the preferred browser for Broadcast        *   FILE 816
//*           Datasets - see File 135 for load modules, or CBT      *   FILE 816
//*           File 134 for source code.)  ISPF Browse leaves off    *   FILE 816
//*           the last byte of the Broadcast Dataset, which you     *   FILE 816
//*           often have to look at, to trace message chains.       *   FILE 816
//*           The Broadcast Dataset is a keyed dataset with key     *   FILE 816
//*           length 1, and ISPF BROWSE is confused by that,        *   FILE 816
//*           leaving off the last data byte of the record.         *   FILE 816
//*           REVIEW knows the difference between keys and data.    *   FILE 816
//*           And with REVIEW, you see the entire key and all       *   FILE 816
//*           the data.                                             *   FILE 816
//*                                                                 *   FILE 816
```
