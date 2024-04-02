# ollama-typhoon-7b
https://huggingface.co/scb10x/typhoon-7b/tree/f28580fc505e664cf13c11bcc0059ef839354837

Credits:
- https://huggingface.co/scb10x/typhoon-7b
- https://github.com/ollama/ollama


## How to recreate
```bash
git clone https://huggingface.co/scb10x/typhoon-7b
python ollama/llm/llama.cpp/convert.py ./typhoon-7b --outtype f16 --outfile typhoon-7b.bin
ollama/llm/llama.cpp/quantize typhoon-7b.bin typhoon-7b-q4_0.bin q4_0
ollama/llm/llama.cpp/quantize typhoon-7b.bin typhoon-7b-q8_0.bin q8_0

split -b 2g typhoon-7b.bin typhoon-7b.bin.split.
split -b 2g typhoon-7b-q4_0.bin typhoon-7b-q4_0.bin.split.
split -b 2g typhoon-7b-q8_0.bin typhoon-7b-q8_0.bin.split.

rm -rf typhoon-7b.bin typhoon-7b-q4_0.bin typhoon-7b-q8_0.bin

cat typhoon-7b.bin.split.* > typhoon-7b.bin
cat typhoon-7b-q4_0.bin.split.* > typhoon-7b-q4_0.bin
cat typhoon-7b-q8_0.bin.split.* > typhoon-7b-q8_0.bin

```

