# eBlocks Online - Development Changelog

## Current Task
**Status:** ready-to-start  
**Last Agent:** Initial setup - 2026-02-22 21:28 UTC  
**Next Step:** Convert Electron app to web-based IDE using Monaco Editor + JSCPP + Web Serial API

## Architecture Overview
**Goal:** Pure static GitHub Pages app - no backend dependencies

**Components:**
1. **Monaco Editor** - VS Code-like C++ editor with syntax highlighting
2. **JSCPP Interpreter** - Run C++ code as JavaScript in browser
3. **Web Serial API** - Direct browser-to-board USB communication
4. **Firmata Protocol** - Pre-flashed on boards to receive commands

**Hardware Flow:**
- Arduino boards: Pre-flash with StandardFirmata
- ESP32 boards: Pre-flash with Firmata or custom JSON serial handler
- User connects via Web Serial (Chrome/Edge only)
- C++ code transpiled → Firmata commands → USB → Board

## Blockers
None yet.

## Progress Log
- **2026-02-22 21:28 UTC:** Repository created, initial structure cloned from eblocks-companion-app
- **Next:** Start conversion to web app - integrate Monaco Editor

## Technical Notes
**Browser Support:** Chrome/Edge only (Web Serial API limitation)
**Safeguards Needed:**
- Infinite loop detection (Web Worker isolation)
- Force yield every 1ms in loops
- Timeout protection for runaway code

**Key Libraries:**
- Monaco Editor: https://microsoft.github.io/monaco-editor/
- JSCPP: https://github.com/felixhao28/JSCPP
- Web Serial: https://developer.mozilla.org/en-US/docs/Web/API/Web_Serial_API
