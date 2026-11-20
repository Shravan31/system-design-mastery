# Video Platform

## Problem
Upload, process, store, and stream videos.

## Functional scope
- [ ] Upload video
- [ ] Transcode variants
- [ ] Playback
- [ ] Metadata and search

## Design concerns
- [ ] Object storage
- [ ] Transcoding queue
- [ ] CDN
- [ ] Adaptive bitrate
- [ ] Large file uploads

## Deliverables
- [ ] Upload sequence
- [ ] Processing pipeline
- [ ] Storage estimate
- [ ] Playback architecture

## Design review questions
- What assumptions did I make?
- What is the critical request or event path?
- What fails first as traffic grows 10x?
- What data can be stale, and for how long?
- How does the system recover from partial failure?
- Which parts are intentionally simple for this learning project?
