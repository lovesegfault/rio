install:
	cargo install cargo-server
	cargo install wasm-bindgen-cli
	cargo install cargo-watch

run: build
	cargo server --open

opt:
	# https://github.com/WebAssembly/binaryen
	du -h ./wasm/sugarloaf_styled_text_bg.wasm
	wasm-opt -O ./wasm/sugarloaf_styled_text_bg.wasm -o ./wasm/sugarloaf_styled_text_bg.wasm
	du -h ./wasm/sugarloaf_styled_text_bg.wasm

watch:
	cargo watch -- make build

build:
	cargo build -p sugarloaf-styled-text --target wasm32-unknown-unknown
	wasm-bindgen ../../target/wasm32-unknown-unknown/debug/sugarloaf_styled_text.wasm --out-dir wasm --target web --no-typescript

build-release:
	cargo build -p sugarloaf-styled-text --target wasm32-unknown-unknown --release
	wasm-bindgen ../../target/wasm32-unknown-unknown/release/sugarloaf_styled_text.wasm --out-dir wasm --target web --no-typescript