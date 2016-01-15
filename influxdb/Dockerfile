FROM tutum/influxdb:0.9
MAINTAINER Danilo Bargen <mail@dbrgn.ch>

# Enable authentication
RUN sed -i 's/auth-enabled = false/auth-enabled = true/g' /config/config.toml
