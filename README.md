# Ocr

## Synopsis

Neuron to perform OCR with google cloud vision API

## Installation

```bash
kalliope install --git-url https://github.com/ordimission/kalliope_neuron_ocr
```

## Options

| parameter | required | default | choices                                | comments                                                                         |
|-----------|----------|---------|----------------------------------------|----------------------------------------------------------------------------------|
| lang_out  | yes      |         | E.g: "en", "fr", "Spanish", "Français" | Language to translate sentence: langage code ("en") or language name ("Spanish") |
| lang_in   | no       |  auto   | E.g: "auto", "en", "fr"                | Language of original sentence: "auto" for automatique detection or lang code     |
| image_path  | yes      |         |                                        | Sentence translate                                                               |

[Langage support and ISO-639-1 Code](https://cloud.google.com/translate/docs/languages) 

## Return Values

| Name     | Description           | Type   | sample          |
|----------|-----------------------|--------|-----------------|
| result   | Result of translation | string | "Buenas noches" |
| lang_in  | lang id in            | string | "en"            |
| lang_out | lang id out           | string | "es"            |

## Synapses example with override voice parameter

```yml
- name: "ocr-fr"
  signals:
    - order: "reconnais le texte"
  neurons:
    - translate:
        lang_in: "fr"
        lang_out: "es"
        sentence: "{{sentence}}"
        say_template: 
          - "{{ result }}"
        tts:             
          pico2wave:
            language: "es-ES"
            cache: False
```
