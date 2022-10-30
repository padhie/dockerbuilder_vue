<script setup lang="ts">
export default {
  name: "Output"
}
</script>

<template>
        <pre id="output" class="preview p-3">
version: '3'

services:
  app:
    image: thecodingmachine/nodejs:v2-18-apache-bullseye
    container_name: dockerbuilder_app
    labels:
      - "traefik.http.routers.dockerbuilder.rule=Host(`dockerbuilder.localhost`)"
    volumes:
      - .:/var/www/html
    ports:
      - "5173:5173"
    environment:
      APACHE_EXTENSION_DAV: 1
      APACHE_EXTENSION_SSL: 1
      APACHE_DOCUMENT_ROOT: dist/
    networks:
      traefik:
        ipv4_address: 172.16.31.1

networks:
  traefik:
    external: true
      </pre>
</template>

<style scoped>
.preview {
  background-color: lightgrey;
  border-radius: 10px;
}
</style>
