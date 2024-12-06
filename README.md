# jimw-vllm

```py
(base) xlisp@xlisp:~$ proxy
(base) xlisp@xlisp:~$ ipython
Python 3.12.7 | packaged by Anaconda, Inc. | (main, Oct  4 2024, 13:27:36) [GCC 11.2.0]
Type 'copyright', 'credits' or 'license' for more information
IPython 8.27.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: from vllm import LLM, SamplingParams

In [2]: llm = LLM(model="microsoft/phi-1_5")
INFO 12-06 11:39:30 llm_engine.py:249] Initializing an LLM engine (v0.6.4.post1) with config: model='microsoft/phi-1_5', speculative_config=None, tokenizer='microsoft/phi-1_5', skip_tokenizer_init=False, tokenizer_mode=auto, revision=None, override_neuron_config=None, tokenizer_revision=None, trust_remote_code=False, dtype=torch.float16, max_seq_len=2048, download_dir=None, load_format=LoadFormat.AUTO, tensor_parallel_size=1, pipeline_parallel_size=1, disable_custom_all_reduce=False, quantization=None, enforce_eager=False, kv_cache_dtype=auto, quantization_param_path=None, device_config=cuda, decoding_config=DecodingConfig(guided_decoding_backend='outlines'), observability_config=ObservabilityConfig(otlp_traces_endpoint=None, collect_model_forward_time=False, collect_model_execute_time=False), seed=0, served_model_name=microsoft/phi-1_5, num_scheduler_steps=1, chunked_prefill_enabled=False multi_step_stream_outputs=True, enable_prefix_caching=False, use_async_output_proc=True, use_cached_outputs=False, chat_template_text_format=string, mm_processor_kwargs=None, pooler_config=None)
INFO 12-06 11:39:31 selector.py:261] Cannot use FlashAttention-2 backend for Volta and Turing GPUs.
INFO 12-06 11:39:31 selector.py:144] Using XFormers backend.
INFO 12-06 11:39:31 model_runner.py:1072] Starting to load model microsoft/phi-1_5...
INFO 12-06 11:39:32 weight_utils.py:243] Using model weights format ['*.safetensors']
INFO 12-06 11:39:33 weight_utils.py:288] No model.safetensors.index.json found in remote.
Loading safetensors checkpoint shards:   0% Completed | 0/1 [00:00<?, ?it/s]
Loading safetensors checkpoint shards: 100% Completed | 1/1 [00:01<00:00,  1.15s/it]
Loading safetensors checkpoint shards: 100% Completed | 1/1 [00:01<00:00,  1.15s/it]

INFO 12-06 11:39:34 model_runner.py:1077] Loading model weights took 2.6419 GB
INFO 12-06 11:39:36 worker.py:232] Memory profiling results: total_gpu_memory=7.92GiB initial_memory_usage=3.09GiB peak_torch_memory=3.12GiB memory_usage_post_profile=3.12GiB non_torch_memory=0.47GiB kv_cache_size=3.54GiB gpu_memory_utilization=0.90
INFO 12-06 11:39:36 gpu_executor.py:113] # GPU blocks: 1207, # CPU blocks: 1365
INFO 12-06 11:39:36 gpu_executor.py:117] Maximum concurrency for 2048 tokens per request: 9.43x
INFO 12-06 11:39:39 model_runner.py:1400] Capturing cudagraphs for decoding. This may lead to unexpected consequences if the model is not static. To run the model in eager mode, set 'enforce_eager=True' or use '--enforce-eager' in the CLI.
INFO 12-06 11:39:39 model_runner.py:1404] If out-of-memory error occurs during cudagraph capture, consider decreasing `gpu_memory_utilization` or switching to eager mode. You can also reduce the `max_num_seqs` as needed to decrease memory usage.
INFO 12-06 11:40:01 model_runner.py:1518] Graph capturing finished in 21 secs, took 0.54 GiB

In [3]: llm.generate("who are you?")
Processed prompts: 100%|███████████████| 1/1 [00:00<00:00,  3.00it/s, est. speed input: 12.00 toks/s, output: 47.98 toks/s]
Out[3]: [RequestOutput(request_id=0, prompt='who are you?', prompt_token_ids=[8727, 389, 345, 30], encoder_prompt=None, encoder_prompt_token_ids=None, prompt_logprobs=None, outputs=[CompletionOutput(index=0, text=' � disagreement!!!!!!!!!!!!!!', token_ids=(564, 25800, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0), cumulative_logprob=None, logprobs=None, finish_reason=length, stop_reason=None)], finished=True, metrics=RequestMetrics(arrival_time=1733456759.553771, last_token_time=1733456759.553771, first_scheduled_time=1733456759.5569673, first_token_time=1733456759.6604152, time_in_queue=0.003196239471435547, finished_time=1733456759.8888953, scheduler_time=0.0018781600001602783, model_forward_time=None, model_execute_time=None), lora_request=None, num_cached_tokens=0)]

```
