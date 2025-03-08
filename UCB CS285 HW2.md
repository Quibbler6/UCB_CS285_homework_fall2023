## UCB CS285 HW2

### Policy Gradients  Experiments

```bash
python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 1000 
--exp_name cartpole

python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 1000 
-rtg --exp_name cartpole_rtg

python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 1000 
-na --exp_name cartpole_na

python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 1000 
-rtg -na --exp_name cartpole_rtg_na


python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 4000 
--exp_name cartpole_lb

python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 4000 
-rtg --exp_name cartpole_lb_rtg

python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 4000 
-na --exp_name cartpole_lb_na

python cs285/scripts/run_hw2.py --env_name CartPole-v0 -n 100 -b 4000 
-rtg -na --exp_name cartpole_lb_rtg_na
```

Learning curves (average return vs. number of environment steps)for the experiments prefixed with cartpole

![image-20250221201226151](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250221201226151.png)

```bash
# No baseline
python cs285/scripts/run_hw2.py --env_name HalfCheetah-v4 
-n 100 -b 5000 -rtg --discount 0.95 -lr 0.01 
--exp_name cheetah
# Baseline
python cs285/scripts/run_hw2.py --env_name HalfCheetah-v4 
-n 100 -b 5000 -rtg --discount 0.95 -lr 0.01 
--use_baseline -blr 0.01 -bgs 5 --exp_name cheetah_baseline

python cs285/scripts/run_hw2.py --env_name HalfCheetah-v4 
-n 100 -b 5000 -rtg --discount 0.95 -lr 0.01 
--use_baseline -blr 0.001 -bgs 5 --exp_name cheetah_baseline_small_blr

python cs285/scripts/run_hw2.py --env_name HalfCheetah-v4 
-n 100 -b 5000 -rtg --discount 0.95 -lr 0.01 
--use_baseline -blr 0.01 -bgs 1 --exp_name cheetah_baseline_small_bgs

python cs285/scripts/run_hw2.py --env_name HalfCheetah-v4 
-n 100 -b 5000 -rtg --discount 0.95 -lr 0.01 
--use_baseline -blr 0.01 -bgs 5 -na --video_log_freq 10 --exp_name cheetah_baseline
```

```bash
python cs285/scripts/run_hw2.py 
--env_name LunarLander-v2 --ep_len 1000 
--discount 0.99 -n 300 -l 3 -s 128 -b 2000 -lr 0.001 
--use_reward_to_go --use_baseline --gae_lambda 0.95 
--exp_name lunar_lander_lambda_0.95
```

