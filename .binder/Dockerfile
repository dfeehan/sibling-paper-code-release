FROM rocker/binder:4.0.2
LABEL maintainer='Dennis M. Feehan'

ARG NB_USER=rstudio

USER root
COPY . ${HOME}

RUN chown -R ${NB_USER} ${HOME}

# this hack appears to fix the permissions problems...
RUN chown -R ${NB_USER} /home/${NB_USER}

USER ${NB_USER}

RUN wget https://github.com/dfeehan/sibling-paper-code-release/raw/main/DESCRIPTION && R -e "options(repos = list(CRAN = 'http://mran.revolutionanalytics.com/snapshot/2020-11-16/')); devtools::install_deps()"

RUN rm DESCRIPTION.1; exit 0
