FROM hub.slyak.com/common-debain-openjdk
COPY tesseract-3.05.zip /
RUN set -x \
        && apt-get install -y --no-install-recommends \
        autoconf-archive \
        automake \
        g++ \
        libtool \
        libleptonica-dev \
        pkg-config \
        libpango1.0-dev \
        git \
        && unzip /tesseract-3.05.zip \
        && rm /tesseract-3.05.zip \
        && cd /tesseract-3.05 \
        && ./autogen.sh \
        && ./configure \
        && make \
        && make install \
        && make training \
        && make training-install \
        && ldconfig \
        && apt-get clean \
        && rm -rf /tesseract-3.05 /var/lib/apt/lists/*

COPY chi_sim.traineddata /usr/local/share/tessdata/
COPY eng.traineddata /usr/local/share/tessdata/

VOLUME ["/usr/local/share/tessdata/"]