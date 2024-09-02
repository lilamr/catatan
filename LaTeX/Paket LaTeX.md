The table below shows the size of archives that would be downloaded and the additional disk space that would be used for each package installed with `apt-get install` command. Each size displayed include the size of the package being installed and the size of all dependencies that would be installed along with it.

### Package Sizes

```latex
Package                    Archives  Disk Space
-------------------------  --------  ----------
texlive-latex-base            59 MB      216 MB
texlive-latex-recommended     74 MB      248 MB
texlive-pictures              83 MB      277 MB
texlive-fonts-recommended     83 MB      281 MB
texlive                       98 MB      314 MB
texlive-plain-generic         82 MB      261 MB
texlive-latex-extra          144 MB      452 MB
texlive-full                2804 MB     5358 MB
```

### Package Details

- `texlive-latex-base`: This package contains packages that are either mandated by the core LaTeX team, or very widely used and strongly recommended in practice.
    
    It includes 28 CTAN packages:
    
    ```latex
    ae, amscls, amsmath, babel, babel-english, babelbib, carlisle, colortbl, fancyhdr, fix2col, geometry, graphics, graphics-cfg, hyperref, latex, latex-bin, latex-fonts, latexconfig, ltxmisc, mfnfss, mptopdf, natbib, oberdiek, pslatex, psnfss, pspicture, tools, url
    ```
    
- `texlive-latex-recommended`: It contains a collection of recommended add-on packages for LaTeX which have widespread use.
    
    Installing this package also installs `texlive-latex-base` because `texlive-latex-recommended` recommends `tipa` which depends on `texlive-latex-base`.
    
    It includes 62 CTAN packages:
    
    ```latex
    anysize, beamer, booktabs, breqn, caption, cite, cmap, crop, ctable, eso-pic, euenc, euler, etoolbox, extsizes, fancybox, fancyref, fancyvrb, filehook, float, fontspec, fp, index, jknapltx, koma-script, latexbug, l3experimental, l3kernel, l3packages, lineno, listings, lwarp, mathspec, mathtools, mdwtools, memoir, metalogo, microtype, ms, ntgclass, parskip, pdfpages, polyglossia, powerdot, psfrag, rcs, sansmath, section, seminar, sepnum, setspace, subfig, textcase, thumbpdf, translator, typehtml, ucharcat, underscore, unicode-math, xcolor, xkeyval, xltxtra, xunicode.
    ```
    
- `texlive-pictures`: It contains packages for graphics, pictures, and diagrams including TikZ, pict, etc.
    
    Installing this package also installs `texlive-latex-base` and `texlive-latex-recommended` because this package depends on `texlive-latex-recommended` which in turn depends on `texlive-latex-base`.
    
    It includes 188 CTAN packages:
    
    ```latex
    adigraph, aobs-tikz, askmaps, asyfig, asypictureb, autoarea, bardiag, beamerswitch, binarytree, blochsphere, bloques, blox, bodegraph, bondgraph, bondgraphs, braids, bxeepic, cachepic, callouts, celtic, chemfig, combinedgraphics, circuitikz, curve, curve2e, curves, dcpic, diagmac2, ditaa, doc-pictex, dottex, dot2texi, dratex, drs, duotenzor, dynkin-diagrams, ecgdraw, eepic, ellipse, endofproofwd, epspdf, epspdfconversion, esk, euflag, fast-diagram, fig4latex, fitbox, flowchart, forest, genealogytree, getmap, gincltex, gnuplottex, gradientframe, grafcet, graph35, graphicxpsd, graphviz, gtrlib-largetrees, harveyballs, here, hf-tikz, hobby, hvfloat, istgame, knitting, knittingpattern, ladder, lapdf, latex-make, lpic, lroundrect, luamesh, luasseq, maker, makeshape, mathspic, milsymb, miniplot, mkpic, modiagram, neuralnetwork, numericplots, pb-diagram, penrose, petri-nets, pgf, pgf-blur, pgf-cmykshadings, pgf-soroban, pgf-spectra, pgf-umlcd, pgf-umlsd, pgfgantt, pgfkeyx, pgfmolbio, pgfopts, pgfornament, pgfplots, picinpar, pict2e, pictex, pictex2, pinlabel, pixelart, pmgraph, postage, prerex, productbox, pxpgfmark, qcircuit, quantikz, qrcode, randbild, randomwalk, realhats, reotex, rviewport, sa-tikz, schemabloc, scsnowman, scratch, scratch3, setdeck, signchart, smartdiagram, spath3, spectralsequences, swimgraf, table-fct, texdraw, ticollege, tipfr, tikz-3dplot, tikz-bayesnet, tikz-cd, tikz-dependency, tikz-dimline, tikz-feynhand, tikz-feynman, tikz-imagelabels, tikz-inet, tikz-kalender, tikz-karnaugh, tikz-ladder, tikz-layers, tikz-nef, tikz-network, tikz-opm, tikz-optics, tikz-page, tikz-palattice, tikz-qtree, tikz-relay, tikz-sfc, tikz-timing, tikz-truchet, tikzcodeblocks, tikzducks, tikzinclude, tikzlings, tikzmark, tikzmarmots, tikzorbital, tikzpagenodes, tikzpfeile, tikzpeople, tikzposter, tikzscale, tikzsymbols, timing-diagrams, tqft, tkz-base, tkz-berge, tkz-doc, tkz-euclide, tkz-fct, tkz-graph, tkz-kiviat, tkz-linknodes, tkz-orm, tkz-tab, tsemlines, tufte-latex, venndiagram, visualpstricks, xpicture, xypic
    ```
    
- `texlive-fonts-recommended`: This package contains the recommended fonts, including the base 35 PostScript fonts, Latin Modern, TeX Gyre, and T1 and other encoding support for Computer Modern, in outline form.
    
    Installing this package also installs `texlive-latex-base` because it is one of the dependencies of this package.
    
    It includes 24 CTAN packages:
    
    ```latex
    avantgar, bookman, charter, cmextra, courier, ec, euro, euro-ce, eurosym, fpl, helvetic, marvosym, mathpazo, manfnt-font, mflogo-font, ncntrsbk, palatino, pxfonts, rsfs, symbol, times, txfonts, utopia, wasy, wasy2-ps, wasysym, zapfchan, zapfding
    ```
    
- `texlive`: This metapackage provides a decent selection of the TeX Live packages which should suffice for the most common tasks.
    
    This is a metapackage, i.e., it does not include any CTAN packages of its own. It merely depends on `texlive-latex-base`, `texlive-latex-recommended`, and `texlive-fonts-recommended`. In other words, `apt-get install texlive` would be a convenient way to install a trimmed down TeX Live distribution with all the recommended CTAN packages.
    
- `texlive-plain-generic`: This package contains add-on packages and macros that work with plain TeX, often LaTeX, and occasionally other formats.
    
    It includes 91 CTAN packages:
    
    ```latex
    abbr, abstyles, apnum, autoaligne, barr, bitelist, borceux, c-pascal, catcodes, chronosys, colorsep, cweb-old, dinat, dirtree, docbytex, dowith, eijkhout, encxvlna, epigram, epsf, epsf-dvipdfmx, fenixpar, figflow, fixpdfmag, fltpoint, fntproof, font-change, fontch, fontname, gates, genmisc, getoptk, gfnotation, gobble, graphics-pln, gtl, hlist, hyplain, ifetex, iftex, insbox, js-misc, kastrup, lambda-lists, langcode, lecturer, librarian, listofitems, mathdots, metatex, midnight, mkpattern, modulus, multido, navigator, newsletr, ofs, olsak-misc, path, pdf-trans, pitex, placeins-plain, plainpkg, plipsum, plnfss, plstmary, poormanlog, present, randomlist, resumemac, schemata, shade, simplekv, systeme, tabto-generic, termmenu, tex-ps, tex4ht, texapi, texdate, timetable, tracklang, treetex, trigonometry, ulem, upca, varisize, xii, xii-lat, xlop, yax
    ```
    
- `texlive-latex-extra`: This package contains a very large collection of add-on packages.
    
    Installing this package also installs `texlive-latex-base`, `texlive-latex-recommended`, `texlive-pictures`, `texlive-fonts-recommended`, and `texlive-plain-generic`. This package depends on `texlive-latex-recommended` (which in turn depends on `texlive-latex-base`) and `texlive-pictures`. Further, this package recommends `texlive-plain-generic` and `texlive-fonts-recommended`.
    
    It includes 1239 CTAN packages:
    
    ```latex
    2up, ESIEEcv, GS1, HA-prosper, Tabbing, a0poster, a4wide, a5comb, abraces, abstract, achemso, acro, acronym, acroterm, actuarialangle, actuarialsymbol, addfont, addlines, adjmulticol, adjustbox, adrconv, advdate, akktex, akletter, alertmessage, alnumsec, alterqcm, altfont, amsaddr, animate, anonchap, answers, anyfontsize, appendix, appendixnumberbeamer, apptools, arcs, arrayjobx, arraysort, arydshln, asciilist, assignment, assoccnt, attachfile, aurl, authoraftertitle, authorarchive, authorindex, autonum, autopdf, avremu, axessibility, background, bankstatement, bashful, basicarith, bchart, beamer2thesis, beameraudience, beamercolorthemeowl, beamerdarkthemes, beamerposter, beamersubframe, beamertheme-cuerna, beamertheme-detlevcm, beamertheme-epyt, beamertheme-focus, beamertheme-light, beamertheme-metropolis, beamertheme-npbt, beamertheme-phnompenh, beamertheme-saintpetersburg, beamertheme-upenn-bc, beamerthemejltree, beamerthemenirma, beton, bewerbung, bez123, bezos, bhcexam, bibletext, bigfoot, bigints, biochemistry-colors, bizcard, blindtext, blkarray, block, blowup, bnumexpr, boites, bold-extra, bookcover, bookest, booklet, boolexpr, bophook, boxedminipage, boxedminipage2e, boxhandler, bracketkey, braket, breakurl, bullcntr, bussproofs, bxcalc, bxdpx-beamer, bxdvidriver, bxenclose, bxnewfont, bxpapersize, bxpdfver, bxtexlogo, calcage, calctab, calculator, calrsfs, cals, calxxxx-yyyy, cancel, canoniclayout, capt-of, captcont, captdef, carbohydrates, cases, casyl, catchfilebetweentags, catechis, catoptions, cbcoptic, ccaption, cclicenses, cd, cd-cover, cdpbundl, cellprops, cellspace, censor, changebar, changelayout, changelog, changepage, changes, chappg, chapterfolder, cheatsheet, chet, chextras, childdoc, chkfloat, chletter, chngcntr, chronology, circ, classics, classpack, clefval, cleveref, clipboard, clock, cloze, clrdblpg, clrstrip, cmdstring, cmdtrack, cmsd, cnltx, cntformats, cntperchap, codedoc, codepage, codesection, collcell, collectbox, colophon, colordoc, colorinfo, coloring, colorspace, colortab, colorwav, colorweb, colourchange, combelow, combine, comma, commado, commedit, comment, competences, concepts, concprog, constants, continue, contour, contracard, conv-xkv, cooking, cooking-units, cool, coollist, coolstr, coolthms, cooltooltips, coordsys, copyedit, copyrightbox, coseoul, counttexruns, courseoutline, coursepaper, coverpage, cprotect, crbox, crossreference, crossreftools, csquotes, css-colors, csvsimple, cuisine, currency, currfile, currvita, cutwin, cv, cv4tw, cweb-latex, cyber, cybercic, dashbox, dashrule, dashundergaps, dataref, datatool, dateiliste, datenumber, datetime, datetime2, datetime2-bahasai, datetime2-basque, datetime2-breton, datetime2-bulgarian, datetime2-catalan, datetime2-croatian, datetime2-czech, datetime2-danish, datetime2-dutch, datetime2-en-fulltext, datetime2-english, datetime2-esperanto, datetime2-estonian, datetime2-finnish, datetime2-french, datetime2-galician, datetime2-german, datetime2-greek, datetime2-hebrew, datetime2-icelandic, datetime2-irish, datetime2-italian, datetime2-it-fulltext, datetime2-latin, datetime2-lsorbian, datetime2-magyar, datetime2-norsk, datetime2-polish, datetime2-portuges, datetime2-romanian, datetime2-russian, datetime2-samin, datetime2-scottish, datetime2-serbian, datetime2-slovak, datetime2-slovene, datetime2-spanish, datetime2-swedish, datetime2-turkish, datetime2-ukrainian, datetime2-usorbian, datetime2-welsh, dblfloatfix, decimal, decorule, delimtxt, denisbdoc, diagbox, diagnose, dialogl, dichokey, dinbrief, directory, dirtytalk, dlfltxb, dnaseq, doclicense, docmfp, docmute, doctools, documentation, doi, dotarrow, dotseqn, download, dox, dpfloat, dprogress, drac, draftcopy, draftfigure, draftwatermark, dtk, dtxdescribe, dtxgallery, duckuments, ducksay, dvdcoll, dynamicnumber, dynblocks, ean13isbn, easy, easy-todo, easyfig, easyformat, easylist, easyreview, ebezier, ecclesiastic, ecv, ed, edmargin, eemeir, efbox, egplot, elegantbook, elegantnote, elegantpaper, elements, ellipsis, elmath, elocalloc, elpres, elzcards, emarks, embedall, embrac, emptypage, emulateapj, endfloat, endheads, endnotes, engpron, engrec, enotez, enumitem, enumitem-zref, envbig, environ, envlab, epigraph, epiolmec, eqell, eqlist, eqnalign, eqname, eqparbox, errata, erw-l3, esami, esdiff, esint, esint-type1, etaremune, etextools, etoc, eukdate, eulerpx, europasscv, europecv, everyhook, everypage, exam, exam-n, exam-randomizechoices, examdesign, exframe, example, examplep, exceltex, excludeonly, exercise, exercisebank, exercisepoints, exercises, exp-testopt, expdlist, export, exsheets, exsol, extract, facsimile, factura, fancyhandout, fancylabel, fancynum, fancypar, fancyslides, fancytabs, fancytooltips, fcolumn, fetchcls, ffslides, fgruler, fibeamer, fifo-stack, figsize, filecontents, filecontentsdef, filedate, fileinfo, filemod, fink, finstrut, fithesis, fixcmex, fixfoot, fixme, fixmetodonotes, fjodor, flabels, flacards, flagderiv, flashcards, flashmovie, flipbook, flippdf, floatflt, floatrow, flowfram, fmp, fmtcount, fn2end, fnbreak, fncychap, fncylab, fnpara, fnpct, fnumprint, foilhtml, fontaxes, fonttable, footmisc, footmisx, footnotebackref, footnotehyper, footnoterange, footnpag, forarray, foreign, forloop, formlett, forms16be, formular, fragments, frame, framed, frankenstein, frege, ftcap, ftnxtra, fullblck, fullminipage, fullwidth, fundus-calligra, fundus-cyr, fundus-sueterlin, fvextra, fwlw, g-brief, gatherenum, gauss, gcard, gcite, gender, genmpage, getfiledate, getitems, ginpenc, gitfile-info, gitinfo, gitinfo2, gitlog, gitver, globalvals, gloss, glossaries, glossaries-danish, glossaries-dutch, glossaries-english, glossaries-estonian, glossaries-extra, glossaries-finnish, glossaries-french, glossaries-german, glossaries-irish, glossaries-italian, glossaries-magyar, glossaries-polish, glossaries-portuges, glossaries-serbian, glossaries-spanish, gmdoc, gmdoc-enhance, gmiflink, gmutils, gmverb, grabbox, graphbox, graphicx-psmin, graphicxbox, grayhints, grfpaste, grid, grid-system, gridset, gridslides, guitlogo, halloweenmath, hackthefootline, handin, handout, hang, hanging, hardwrap, harnon-cv, harpoon, hc, he-she, hhtensor, histogr, hitec, hletter, hpsdiss, hrefhide, hvindex, hypdvips, hyper, hyperbar, hypernat, hyperxmp, hyphenat, identkey, idxcmds, idxlayout, iffont, ifmslide, ifmtarg, ifnextok, ifoddpage, ifplatform, ifthenx, iitem, image-gallery, imakeidx, import, incgraph, indextools, inline-images, inlinedef, inputtrc, interactiveworkbook, interfaces, intopdf, inversepath, invoice, invoice-class, invoice2, iso, iso10303, isodate, isodoc, isonums, isopt, isorot, isotope, issuulinks, iwhdp, jlabels, jslectureplanner, jumplines, jvlisting, kalendarium, kantlipsum, kerntest, keycommand, keyfloat, keyreader, keystroke, keyval2e, keyvaltable, kix, knowledge, koma-moderncvclassic, koma-script-sfs, komacv, komacv-rg, ktv-texdata, l3build, labbook, labels, labelschanged, lastpackage, lastpage, latex-tds, latex-uni8, latexcolors, latexdemo, latexgit, layouts, lazylist, lccaps, lcd, lcg, leading, leaflet, lectures, leftidx, leipzig, lengthconvert, lettre, lettrine, lewis, lhelp, libgreek, limap, linegoal, linop, lipsum, lisp-on-tex, listing, listlbls, listliketab, listofsymbols, lkproof, lmake, locality, localloc, logbox, logical-markup-utils, logpap, longfbox, longfigure, longnamefilelist, loops, lsc, lstaddons, lstfiracode, lt3graph, ltablex, ltabptch, ltxdockit, ltxguidex, ltxindex, ltxkeys, ltxnew, ltxtools, lua-check-hyphen, luatodonotes, macroswap, magaz, makecookbook, mailing, mailmerge, makebarcode, makebase, makebox, makecell, makecirc, makecmds, makedtx, makeglos, mandi, manfnt, manuscript, manyind, marginfit, marginfix, marginnote, markdown, mathalfa, mathastext, mathexam, mathfam256, mathfont, maybemath, mbenotes, mcaption, mceinleger, mcexam, mcite, mciteplus, mdframed, media9, medstarbeamer, meetingmins, memexsupp, memory, mensa-tex, menu, menukeys, metalogox, method, metre, mfirstuc, mftinc, mi-solns, midpage, minibox, minidocument, minifp, minipage-marginpar, minitoc, minorrevision, minted, minutes, mla-paper, mlist, mmap, mnotes, moderncv, modernposter, moderntimeline, modref, modroman, modular, monofill, moodle, moreenum, morefloats, morehype, moresize, moreverb, morewrites, movie15, mparhack, mpostinl, msc, msg, mslapa, mtgreek, multenum, multiaudience, multibbl, multicap, multicolrule, multidef, multienv, multiexpand, multilang, multirow, mversion, mwe, mycv, mylatexformat, nag, nameauth, namespc, ncclatex, ncctools, needspace, nestquot, newcommand, newenviron, newfile, newlfm, newspaper, newunicodechar, newvbtm, newverbs, nextpage, nfssext-cfr, nicefilelist, niceframe, nicetext, nidanfloat, nlctdoc, noconflict, noindentafter, noitcrul, nolbreaks, nomencl, nomentbl, nonfloat, nonumonpart, nopageno, normalcolor, notes, notespages, notestex, notoccite, nowidow, nox, ntheorem, numberedblock, numname, numprint, numspell, ocg-p, ocgx, ocgx2, ocr-latex, octavo, oldstyle, onlyamsmath, opcit, optidef, optional, options, outline, outliner, outlines, outlining, overlays, overpic, padcount, pagecolor, pagecont, pagenote, pagerange, pageslts, paper, papercdcase, papermas, papertex, paracol, parades, paralist, paresse, parnotes, parselines, pas-cours, pas-cv, pas-tableur, patch, patchcmd, pauldoc, pawpict, pax, pbox, pbsheet, pdf14, pdfcomment, pdfcprot, pdfmarginpar, pdfoverlay, pdfpagediff, pdfpc-movie, pdfprivacy, pdfreview, pdfscreen, pdfslide, pdfsync, pdfwin, pdfx, pecha, perltex, permute, petiteannonce, phffullpagefigure, phfnote, phfparen, phfqit, phfquotetext, phfsvnwatermark, phfthm, philex, phonenumbers, photo, piff, pkgloader, placeins, plantslabels, plates, plweb, polynom, polynomial, polytable, postcards, poster-mac, ppr-prv, preprint, pressrelease, prettyref, printlen, probsoln, program, progress, progressbar, proofread, properties, prosper, protex, protocol, psfragx, pstool, pstring, pxgreeks, pygmentex, python, qcm, qstest, qsymbols, quicktype, quotchap, quoting, quotmark, ran_toks, randtext, rccol, rcs-multi, rcsinfo, readarray, realboxes, recipe, recipebook, recipecard, rectopma, refcheck, refenums, reflectgraphics, refman, refstyle, regcount, regexpatch, register, regstats, relenc, relsize, repeatindex, repltext, returntogrid, rgltxdoc, rjlparshap, rlepsf, rmpage, robustcommand, robustindex, romanbar, romanbarpagenumber, romanneg, romannum, rotfloat, rotpages, roundbox, rterface, rtkinenc, rulercompass, rvwrite, sanitize-umlaut, sauerj, savefnmark, savesym, savetrees, scale, scalebar, scalerel, scanpages, scrlttr2copy, sdrt, secdot, sectionbox, sectionbreak, sectsty, seealso, selectp, semantic, semantic-markup, semioneside, semproc, sepfootnotes, seqsplit, sesstime, sf298, sffms, sfmath, shadethm, shadow, shadowtext, shapepar, shdoc, shipunov, shorttoc, show2e, showcharinbox, showdim, showexpl, showhyphens, showlabels, sidecap, sidenotes, silence, simplecd, simplecv, simpleinvoice, sitem, skb, skdoc, skeycommand, skeyval, skrapport, slantsc, smalltableof, smartunits, smartref, snapshot, snotez, soul, spark-otf, sparklines, sphack, splitindex, spot, spotcolor, spreadtab, spverbatim, srbook-mem, srcltx, sseq, sslides, stack, stackengine, standalone, stdclsdv, stealcaps, stdpage, stex, storebox, storecmd, stringstrings, sttools, stubs, studenthandouts, subdepth, subeqn, subeqnarray, subfigmat, subfigure, subfiles, subfloat, substitutefont, substr, supertabular, svg, svgcolor, svn, svn-multi, svn-prov, svninfo, syntax, syntrace, synttree, tabfigures, tableaux, tablefootnote, tableof, tablestyles, tablists, tabls, tablvar, tabstackengine, tabto-ltx, tabu, tabularborder, tabularcalc, tabularew, tabulary, tagging, tagpair, tagpdf, talk, tamefloats, tasks, tcldoc, tcolorbox, tdclock, technics, ted, templatetools, termcal, termlist, testhyphens, testidx, tex-label, tex-locale, texlogos, texmate, texments, texpower, texshade, texvc, textfit, textmerg, textpos, textualicomma, theoremref, thinsp, thmtools, threadcol, threeparttable, threeparttablex, thumb, thumbs, thumby, ticket, titlecaps, titlefoot, titlepic, titleref, titlesec, titling, tocbibind, tocdata, tocloft, tocvsec2, todo, todonotes, tokenizer, toolbox, topfloat, topiclongtable, totcount, totpages, translations, trfsigns, trimspaces, trivfloat, trsym, truncate, tucv, turnthepage, twoinone, twoup, txgreeks, type1cm, typed-checklist, typeface, typoaid, typogrid, uassign, ucs, uebungsblatt, umoline, underlin, underoverlap, undolabl, units, unravel, upmethodology, upquote, uri, ushort, uspace, uwmslide, variablelm, varindex, varsfromjobname, varwidth, vdmlisting, verbasef, verbatimbox, verbatimcopy, verbdef, verbments, version, versions, versonotes, vertbars, vgrid, vhistory, vmargin, volumes, vpe, vruler, vwcol, wallcalendar, wallpaper, warning, warpcol, was, widetable, widows-and-orphans, williams, withargs, wordcount, wordlike, worksheet, wrapfig, wtref, xargs, xassoccnt, xbmks, xcntperchap, xcolor-material, xcolor-solarized, xcomment, xcookybooky, xdoc, xellipsis, xfakebold, xfor, xhfill, xifthen, xint, xltabular, xmpincl, xnewcommand, xoptarg, xpatch, xpeek, xprintlen, xpunctuate, xsavebox, xsim, xstring, xtab, xurl, xwatermark, xytree, yafoot, yaletter, yagusylo, ycbook, ydoc, yplan, zebra-goodies, zed-csp, ziffer, zwgetfdate, zwpagelayout
    ```
    
- `texlive-full`: This metapackage pulls all components of TeX Live.
    
    Installing this metapackage installs all the packages discussed above and much more. This metapackage depends on all Tex Live packages including all the above packages.
    

### Dependency Graph

Here's a dependency graph which shows how the various Debian packages for TeX Live depend on each other.

```latex
                      texlive-latex-extra
                         |   |   :   :
       +-----------------+   |   :   :..................
       |                     |   :                     :
       v                     |   :                     v
texlive-pictures             |   :           texlive-plain-generic
       |                     |   :
       |    +----------------+   :...............
       |    |                                   :
       |    |              texlive              :
       |    |               | | |               :
       |    |    +----------+ | +----------+    :
       |    |    |            |            |    :
       v    v    v            |            v    v
texlive-latex-recommended     |  texlive-fonts-recommended
                 |            |            :
                 |            |            v
                 |            |           tipa
                 |            |            |
                 +----------+ | +----------+
                            | | |
                            v v v
                     texlive-latex-base
```

Here's the legend for the above graph:

```latex
      A                       A
      |                       :
      v                       v
      B                       B

A depends on B          A recommends B
```

The `texlive-full` package depends on all of the packages shown above (except `texlive` of course because that's a metapackage).

### Installation Choices

Considering everything I have mentioned above, I see the following good choices for installing TeX Live on Debian or Ubuntu.

- `apt-get install texlive-base`: This is a tiny installation. It downloads only 59 MB of archives and occupies only 216 MB of disk space. It is sufficient for only very basic and straightforward typesetting. Someone who has just started learning LaTeX may be able to perform their learning activities with this minimal installation. But it may not suffice for someone who creates presentations (`beamer` is missing), includes syntax-highlighted code blocks (`listings` and `xcolor` are missing), adds vertical space between paragraphs (`parskip` is missing), or customizes captions (`caption` is missing).
    
- `apt-get install texlive`: This is a small installation. It downloads only 98 MB of archives and occupies 314 MB of disk space. It includes most of the useful stuff like `beamer`, `listings`, `xcolor`, `parskip`, `caption`, etc. I think one can go a long way with this installation. However, it may not be sufficient if you want to draw diagrams with TikZ (`pgf` is missing), or if you want to customize the section headings (`titlesec` is missing), or if you want to place boxes at absolute positions (`textpos` is missing).
    
- `apt-get install texlive-latex-extra`: This is a medium installation. It downloads 144 MB of archives and occupies 452 MB of disk space. It includes a lot of packages. Almost all frequently used stuff are present. For example, `pgf`, `titlesec`, and `textpos` are present. This is what I usually install. Even with the large number of packages, it has a few useful things missing that I occassionally rely on. For example, I cannot include pretty icons with it (`fontawesome` is missing). For such things, I install them separately with `tlmgr`.
    
- `apt-get install texlive-full`: This is a huge installation. It downloads 2.7 GB of archives and occupies 5.2 GB of disk space on installation. Once installed, we are all set for all kinds of typesetting work. We almost never have to worry about missing packages again.

A very short summary of all the texlive packages can be found with `apt-cache search texlive`

As for which package to install, this depends very much on what you are planing on using them for. In my case I installed `texlive-full` as I'm writing articles in several fields, making presentations, etc. and didn't want to spend the time individually installing packages. You can always just start with `texlive-latex-base` and then just install the collections you need. (To find a collection with a package in use `apt-cache search package`) There is no good way yet to install individual packages in Ubuntu, as `tlmgr` will run in user mode (installing packages only for one user). There are ways of fixing this, but this requires the installation of texlive from source or a ppa.