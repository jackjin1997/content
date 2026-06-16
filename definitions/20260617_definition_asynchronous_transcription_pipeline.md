---
title: "Asynchronous Transcription Pipeline"
description: "A speech-to-text workflow that submits media, polls job status, and fetches the completed transcript later."
date: 2026-06-17
author: "Jack Jin"
---

# Asynchronous Transcription Pipeline

## Definition

An asynchronous transcription pipeline is a speech-to-text workflow where a
client submits an audio or video file, receives a task identifier immediately,
polls the provider for task status, and retrieves the transcript only after the
provider finishes processing the media.

## Context and Usage

Asynchronous transcription is useful for longer recordings because the client
does not need to keep one long request open while the provider processes the
file. In a Daytona sandbox, this pattern is a good fit for command-line tools:
the sandbox can submit the media, poll at a controlled interval, and write the
finished transcript into the project folder.

The pattern usually has three API calls: create the transcription task, check
the task status, and fetch the result by run identifier. It is common in hosted
AI transcription providers because processing time depends on file size, audio
quality, language, and current service load.
