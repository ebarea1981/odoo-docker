FROM odoo:12.0
MAINTAINER Eduardo Barea Bermudez. <ebarea1981@gmail.com>

# Generate locale C.UTF-8 for postgres and general locale data
ENV LANG C.UTF-8

USER root

RUN set -x; \
        apt-get update \
        && apt-get install -y --no-install-recommends \
            git \
            vim \
            mc \
            libreoffice-writer \
            libreoffice-calc \
        && rm -rf /var/lib/apt/lists/*

RUN pip3 install \
        py3o.template \
        py3o.formats \
        PyPDF2 \
        wdb

RUN pip3 install git+git://github.com/OCA/openupgradelib.git

# Mount /var/lib/odoo to allow restoring filestore and /mnt/extra-addons for users addons
RUN mkdir -p /mnt/odoo \
    && chown -R odoo /mnt/odoo
VOLUME ["/mnt/odoo"]

USER odoo
