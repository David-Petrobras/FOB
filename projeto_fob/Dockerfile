FROM python:3.10-slim

# Instala suporte ao locale pt_BR.UTF-8
RUN apt-get update && apt-get install -y locales \
  && sed -i '/pt_BR.UTF-8/s/^# //g' /etc/locale.gen \
  && locale-gen pt_BR.UTF-8

ENV LANG=pt_BR.UTF-8
ENV LANGUAGE=pt_BR:pt
ENV LC_ALL=pt_BR.UTF-8

WORKDIR /app

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY src/FOB.py ./
COPY data /app/data
COPY images /app/images
COPY .streamlit /app/.streamlit

EXPOSE 8501

CMD ["streamlit", "run", "FOB.py", "--server.port=8501", "--server.enableCORS=false", "--server.enableXsrfProtection=true"]