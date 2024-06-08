\documentclass{article}
\usepackage[document]{ragged2e}
\usepackage[paperheight=3in,paperwidth=5in,margin=.25in]{geometry}
\usepackage{lipsum}%used for spell description fill during testing
\usepackage{nopageno}%suppresses page numbers
\usepackage{multicol}%basic even columns
\usepackage{graphicx}%inserts images
\usepackage{transparent}%allows for the graying out
\usepackage{tikz} %allows for the fancy boxes
\usepackage{setspace}%because long materal lists and spell descriptions
\usetikzlibrary{positioning,shapes.misc,shapes.symbols,shapes}
\usepackage{wrapfig} %wrapping for materials

%Throughout code
\graphicspath{ {./images/} }
\setlength{\parindent}{0pt}
\small
\renewcommand{\familydefault}{\sfdefault}
\setstretch{.75}
%Setting up shortcuts

% MARKING THE CLASSES
\newcommand{\select}[1]{\includegraphics[height=.3in]{#1}\\ \uppercase{\tiny{#1}}}
\newcommand{\noselect}[1]{\transparent{.2}
    \includegraphics[height=.3in]{#1}
    \transparent{1}}
    
\newcommand{\head}[4]{
    \begin{tikzpicture}[
        block/.style={signal,  signal to=east}, minimum height=.18in]
        \node [draw,block,minimum width=1.9in] {\small{#2}};
        \node [block,draw,fill=white,minimum width=2.5in, xshift=-1.9in]{\small{#1}};
        \node [block,draw, fill=white,xshift=-3.2in,minimum height=.25in]{\small{#3}};
        \node [block,xshift=1.1in] {\small{#4}};
    \end{tikzpicture}
}
\newcommand{\leftdeet}[2]{
\overfullrule=0mm
    \begin{tikzpicture}[
        block/.style={signal, draw, signal to=west}]
        \node [block,minimum width=1in] {\scriptsize{#1}};
        \node [shape=chamfered rectangle,minimum width=1.22in,draw, xshift=1in,fill=white] {\footnotesize{#2}};
    \end{tikzpicture}
}
\newcommand{\rightdeet}[2]{
    \overfullrule=0mm
    \begin{tikzpicture}[
        block/.style={signal, draw, signal to=east}]
        \node [block,minimum width=1in] {\scriptsize{#1}};
        \node [shape=chamfered rectangle,minimum width=1.22in,draw, xshift=-1in,fill=white] {\footnotesize{#2}};
    \end{tikzpicture}
}
%text formatting
\newcommand{\texting}[1]{
    \vspace{-4mm}\setlength{\columnsep}{1mm}\begin{multicols}{2}
        #1 
    \end{multicols}
}

%---------------------------------------------
%IF YOU ARE ADAPTING SPELLS TO FIT ON A SINGLE CARD THIS IS THE BEST ORDER TO KEEP IT LOOKING NICE AND THE DESCRIPTION MAKING SENSE
%   1 CHANGE THE FONT SIZE AS LINE 81 describes
%   2 CHANGE THE WORDING ON THE MATERIAL REQUIREMENTS (aim for two lines)
%   3 CHANGE THE SPACING BETWEEN THE DESCRIPTION AND THE CLASS MARKERS TO -2em
%   4 SHORTEN THE DESCRIPTION (some ways in about.txt)
%   5 SHORTEN SPACING BETWEEN THE RANGE/DURATION LINE AND THE DESCRIPTION, HEAD AND LEFT DEET (-.5em)
%   6 YOU'VE DONE ALL THE SPACE FINAGLING YOU CAN THE EASY WAY, CUT WORDS IN THE DESCRIPTION UNTIL IT WORKS
%   * IF SOME OF THE CLASS MARKERS BUT NOT ALL ARE SPILLING OVER OR THERE IS A BLANK CARD FOLLOWING A SPELL, REMOVE \collumnbreak AT THE END OF THE CLASS MARKERS STARTING AT THE END.
%---------------------------------------------
\begin{document}
	\head{test} {abjuration} {1}{}
	\leftdeet{Casting Time}{1 action}
	\tiny{\begin{tikzpicture}[block/.style={ellipse, minimum width=2em,inner sep=.1em,node distance = 3em}]
		\node [block,draw] (V) {\small{V}};
		\node [block,draw,right of=V] (S) {\small{S}};
		\node [block,draw,right of=S] (M) {\small{M}};
		\node [rectangle, text width=1.25in, right of=M, xshift=.4in]{\tiny{a morsel of food}};
\end{tikzpicture}}\\
	\leftdeet{Range}{30 feet}
	\rightdeet{Duration}{24 hours}
	%The default in the xmlToTex.py sets the font size here to \tiny, which gets most things to fit right away, however, that text is hard to read. \scriptsize is legible, but small. \textboxsize is bigger, then \small, and \normalsize is the biggest in the finished .tex files.
	\scriptsize{\texting{This spell lets you convince a code to edit any spell card. Choose a spell card that you can see within range. It must see and hear you. If the card's Intelligence is 4 or higher, the spell fails. Otherwise, the beast must succeed on a Wisdom saving throw or be charmed by you for the spell's duration. If you or one of your companions harms the target, the spell ends.

At Higher Levels: When you cast this spell using a 2nd level spell slot or higher, you can affect one additional beast for each slot level above 1st.}}\vfill 
    %\vfill adds in blank vertical space, which makes the cards with a shorter description have the classes on the bottom. With a longer description, it pushes those images to the next page. First try removing \vfill, then try \vspace{-x} where x is some LaTeX friendly measurement. 2.5 em is about the largest it can go without the images interfering with the text. If that still isn't enough, try 
	\begin{multicols}{8}\begin{center}
		\noselect{Bard}\vfill\null\columnbreak
		\select{Cleric}\vfill\null\columnbreak
		\noselect{Druid}\vfill\null\columnbreak
		\noselect{Paladin}\vfill\null\columnbreak
		\noselect{Ranger}\vfill\null\columnbreak
		\noselect{Sorcerer}\vfill\null\columnbreak
		\noselect{Warlock}\vfill\null\columnbreak
		\noselect{Wizard}\vfill\null\columnbreak
	\end{center}\end{multicols}
\pagebreak

\end{document}
