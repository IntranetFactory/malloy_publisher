FROM oven/bun:1.2.23-debian

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl ca-certificates unzip git \
    openssl libcurl4 libssl3 dnsutils file \
    # Node.js (needed for some tooling) \
    && curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    # DuckDB CLI \
    && curl -L https://install.duckdb.org | bash \
    && ln -sf /root/.duckdb/cli/latest/duckdb /usr/local/bin/duckdb \
    # ADBC Snowflake driver \
    && curl -sSL https://raw.githubusercontent.com/iqea-ai/duckdb-snowflake/main/scripts/install-adbc-driver.sh | bash \
    && ldconfig \
    # Java for API type generation \
    && apt-get install -y --no-install-recommends default-jdk-headless \
    # Cleanup \
    && rm -rf /var/lib/apt/lists/*

ENV PATH="/root/.duckdb/cli/latest:$PATH"
