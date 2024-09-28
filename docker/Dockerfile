FROM frolvlad/alpine-glibc:alpine-3.8_glibc-2.28

# Config the automated install
COPY texlive.profile texlive.profile

# set up packages
## &&
# Remove unnecessary archieves
RUN apk add --no-cache wget perl xz 

RUN wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz && \
  tar -xzf install-tl-unx.tar.gz && \
  install-tl-20*/install-tl --profile=./texlive.profile

RUN apk --no-cache del xz

RUN rm install-tl-unx.tar.gz texlive.profile && \
  rm -r install-tl-20*

# set up path
ENV PATH="/usr/local/texlive/bin/x86_64-linuxmusl:${PATH}"

# TeXLive update
## &&
# TeXLive deps
## &&
# TeXLive packages
## hyphen-* for english/russial lang word wraps support
## xstring for string switch-cases
## latexmk for fast build target
## xetex for xelatex compiler
## t2 for mathtext
## tools for indentfirst
## oberdiek for ifpdf
## bigfoot for perpage
## zapfding for pzdr
## koma-script for tocbasic
## pgf for tikz
## float for floating
## * for -//-
## &&
# Windows fonts
## &&
# Other tools
RUN tlmgr update --self

RUN apk add --no-cache fontconfig

RUN tlmgr install \
  \
  hyphen-english \
  hyphen-russian \
  \
  latexmk \
  xetex \
  polyglossia \
  t2 \
  tools \
  oberdiek \
  bigfoot \
  zapfding \
  xstring \
  datetime \
  nomencl \
  \
  gensymb \
  geometry \
  setspace \
  footmisc \
  tocloft \
  fancyhdr \
  titlesec \
  graphics \
  graphics-cfg \
  caption \
  amsmath \
  amscls \
  enumitem \
  makecell \
  multirow \
  was \
  sistyle \
  xcolor \
  listings \
  ulem \
  hyperref \
  latexconfig \
  url \
  natbib \
  lastpage \
  totcount \
  pdfpages \
  textcase \
  fp \
  extsizes \
  fmtcount \
  koma-script \
  pdflscape \
  multibib \
  cleveref \
  float \ 
  pgf \ 
  mathspec


RUN apk add --no-cache msttcorefonts-installer 

RUN update-ms-fonts

RUN fc-cache -f

RUN apk add --no-cache make g++
