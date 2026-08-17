# DevSynt AutoGram Engine

An automated n8n workflow that turns a folder of Google Drive images into 
AI-captioned Instagram posts, with duplicate-posting prevention via Supabase.

## Pipeline
1. Google Drive Trigger — detects new images in a specific folder
2. Supabase — checks if the image was already posted (dedupe)
3. If new: downloads the image, uploads it to Supabase Storage
4. AI (Groq/Llama 3.3) — generates a caption and hashtags
5. Publishes the post to Instagram via the Facebook Graph API
6. Logs the post back to Supabase for record-keeping

## Tech Stack
- n8n (self-hosted)
- Google Drive API (OAuth2)
- Supabase (Postgres + Storage)
- Groq (Llama 3.3) for AI captioning
- Instagram Graph API (via Facebook Developer App)

## Setup
See `.env.example` for required credentials. You'll need:
- Google Cloud OAuth2 credentials (Drive API enabled)
- A Supabase project (with a `posted_images` table and a public storage bucket)
- A Groq API key
- A Facebook Developer App with Instagram Graph API access, linked to an 
  Instagram Business account and Facebook Page

## Demo
See the included screenshots in `/Images` for the workflow diagram and an 
example published post.
