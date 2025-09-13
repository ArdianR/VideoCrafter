%cd /content
!git clone -b dev https://github.com/camenduru/VideoCrafter
%cd /content/VideoCrafter

!pip install -q decord einops omegaconf pytorch_lightning transformers av xformers gradio timm open_clip_torch kornia

!apt-get -y install -qq aria2
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/vdo/VideoCrafter/resolve/main/Text2Video_1024_v1_0.ckpt -d /content/VideoCrafter/checkpoints/base_1024_v1 -o model.ckpt


%cd /content/VideoCrafter
!sh scripts/run_text2video.sh