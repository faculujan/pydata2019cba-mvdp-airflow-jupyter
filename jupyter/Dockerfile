FROM jupyter/minimal-notebook

## Setup Python environment
ADD requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

RUN set -xe; \
    : disable authentication; \
    echo "c.NotebookApp.token = ''"    >> ${HOME}/.jupyter/jupyter_notebook_config.py; \
    echo "c.NotebookApp.password = ''" >> ${HOME}/.jupyter/jupyter_notebook_config.py; \
    # jupyter labextension install @jupyterlab/celltags; \
    jupyter nbextension enable --py widgetsnbextension;

WORKDIR ${HOME}/work/jupyter
EXPOSE 8888

ENTRYPOINT ["/usr/local/bin/start.sh", "jupyter"]
CMD ["lab"]
