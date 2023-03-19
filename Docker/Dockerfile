FROM --platform=${BUILDPLATFORM} python:latest

EXPOSE 1234

RUN useradd --create-home --shell /bin/bash ctrl \
	&& chown -R ctrl /home/ctrl

RUN python3 -m pip install numpy matplotlib scipy control ipython jupyter notebook

USER ctrl

RUN echo "cd /home/ctrl \
	&& mkdir -p vrt-env/pyctrl \
	&& python3 -m venv vrt-env/pyctrl"
	
# ENV PATH="$PATH:/home/ctrl/.local/bin"
	
RUN mkdir /home/ctrl/repo

WORKDIR /home/ctrl/repo

CMD jupyter notebook --NotebookApp.token='' --ip 0.0.0.0 --port 1234 --allow-root --no-browser

