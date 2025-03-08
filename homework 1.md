# homework 1
## 1 Analysis
### Problem 1
$$
assume\; \pi_{\theta}(s_t\ne\pi^{*}(s_t)|s_t)\leq \epsilon_{s_t}\\
p_{\theta}(s_t)=(1-\epsilon)^t p_{train}(s_t)+(1-(1-\epsilon)^t)p_{mistake}(s_t)\\
|p_{\theta}(s_t)-p_{train}(s_t)|=(1-(1-\epsilon)^t)|p_{mistake}(s_t)-p_{train}(s_t)|
\\ \leq 2(1-(1-\epsilon)^t)\leq 2t\epsilon_{s_t}
$$
From the inequailty given, we have
$$
\mathbb{E}_{p_{\pi^{*}(s)}}\pi_{\theta}(a\ne\pi^{*}(s)|s)=\frac{1}{T}\sum_{t=1}^T\mathbb{E}_{p_{\pi^*(s_t)}}\pi_{\theta}(a_t\ne\pi^*(s_t)|s_t)\leq \epsilon
$$

$$
\sum_{s_t}|p_{\pi_{\theta}}(s_t)-p_{\pi^{*}}(s_t)|\leq 2\epsilon T
$$

## 2 Editing Code

finish code editing

## 3 Behavioral Cloning
```shell
export PYTHONPATH="${PYTHONPATH}:/home/astar/bowieshi/inno1_remote/UCB_CS285/homework_fall2023/hw1"```
export MUJOCO_GL=egl
```
#### Ant
```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Ant.pkl 
--env_name Ant-v4 --exp_name bc_ant --n_iter 1 
--expert_data cs285/expert_data/expert_data_Ant-v4.pkl 
--video_log_freq -1
```
#### HalfCheetah
```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/HalfCheetah.pkl 
--env_name HalfCheetah-v4 --exp_name bc_HalfCheetah --n_iter 1 
--expert_data cs285/expert_data/expert_data_HalfCheetah-v4.pkl 
--video_log_freq -1
```
#### Hopper
```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Hopper.pkl 
--env_name Hopper-v4 --exp_name bc_Hopper --n_iter 1 
--expert_data cs285/expert_data/expert_data_Hopper-v4.pkl 
--video_log_freq -1
```
#### Walker2d
```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--video_log_freq -1
```
### Result
#### Ant
```text
Eval_AverageReturn : 817.486083984375
Eval_StdReturn : 0.0
Eval_MaxReturn : 817.486083984375
Eval_MinReturn : 817.486083984375
Eval_AverageEpLen : 1000.0
Train_AverageReturn : 4681.891673935816
Train_StdReturn : 30.70862278765526
Train_MaxReturn : 4712.600296723471
Train_MinReturn : 4651.18305114816
Train_AverageEpLen : 1000.0
Training Loss : 0.03868953138589859
Train_EnvstepsSoFar : 0
TimeSinceStart : 1.013308048248291
Initial_DataCollection_AverageReturn : 4681.891673935816
```
#### HalfCheetah
```text
Eval_AverageReturn : 3194.975341796875
Eval_StdReturn : 0.0
Eval_MaxReturn : 3194.975341796875
Eval_MinReturn : 3194.975341796875
Eval_AverageEpLen : 1000.0
Train_AverageReturn : 4034.7999834965067
Train_StdReturn : 32.8677631311341
Train_MaxReturn : 4067.6677466276406
Train_MinReturn : 4001.9322203653724
Train_AverageEpLen : 1000.0
Training Loss : 0.044022444635629654
Train_EnvstepsSoFar : 0
TimeSinceStart : 0.9934091567993164
Initial_DataCollection_AverageReturn : 4034.7999834965067
```
#### Hopper
```text
Eval_AverageReturn : 831.6771240234375
Eval_StdReturn : 245.33074951171875
Eval_MaxReturn : 1112.5146484375
Eval_MinReturn : 437.4661560058594
Eval_AverageEpLen : 256.75
Train_AverageReturn : 3717.5129936182307
Train_StdReturn : 0.3530361779417035
Train_MaxReturn : 3717.8660297961724
Train_MinReturn : 3717.159957440289
Train_AverageEpLen : 1000.0
Training Loss : 0.0362093560397625
Train_EnvstepsSoFar : 0
TimeSinceStart : 1.0032446384429932
Initial_DataCollection_AverageReturn : 3717.5129936182307
```
#### Walker2d
```text
Eval_AverageReturn : 439.4566345214844
Eval_StdReturn : 262.7203674316406
Eval_MaxReturn : 1051.1302490234375
Eval_MinReturn : 253.06988525390625
Eval_AverageEpLen : 162.42857142857142
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.06114453449845314
Train_EnvstepsSoFar : 0
TimeSinceStart : 0.9368889331817627
Initial_DataCollection_AverageReturn : 5383.310325177668
```
![P3img1.png](imgs%2FP3img1.png)
### Comparation between hyperparameters
#### raw
```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl
```
```text
Eval_AverageReturn : 439.4566345214844
Eval_StdReturn : 262.7203674316406
Eval_MaxReturn : 1051.1302490234375
Eval_MinReturn : 253.06988525390625
Eval_AverageEpLen : 162.42857142857142
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.06114453449845314
Train_EnvstepsSoFar : 0
TimeSinceStart : 0.9368889331817627
Initial_DataCollection_AverageReturn : 5383.310325177668
```
#### The amount of training steps
```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--num_agent_train_steps_per_iter 5000
```
```text
Eval_AverageReturn : 1494.6796875
Eval_StdReturn : 2096.178466796875
Eval_MaxReturn : 5125.12744140625
Eval_MinReturn : 261.17926025390625
Eval_AverageEpLen : 338.75
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.007453115191310644
Train_EnvstepsSoFar : 0
TimeSinceStart : 7.485743522644043
Initial_DataCollection_AverageReturn : 5383.310325177668
```

```bash
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--num_agent_train_steps_per_iter 10000
```

```
Eval_AverageReturn : 5197.2490234375
Eval_StdReturn : 0.0
Eval_MaxReturn : 5197.2490234375
Eval_MinReturn : 5197.2490234375
Eval_AverageEpLen : 1000.0
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.004637497011572123
Train_EnvstepsSoFar : 0
TimeSinceStart : 24.065428733825684
Initial_DataCollection_AverageReturn : 5383.310325177668
```



#### the amount of expert data provided

```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--batch_size 5000
```
```text
Eval_AverageReturn : 477.63037109375
Eval_StdReturn : 266.7293395996094
Eval_MaxReturn : 1051.1302490234375
Eval_MinReturn : 257.7591247558594
Eval_AverageEpLen : 173.16666666666666
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.06114453449845314
Train_EnvstepsSoFar : 0
TimeSinceStart : 3.896003007888794
Initial_DataCollection_AverageReturn : 5383.310325177668
```
```bash
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--batch_size 10000
```

```
Eval_AverageReturn : 477.63037109375
Eval_StdReturn : 266.7293395996094
Eval_MaxReturn : 1051.1302490234375
Eval_MinReturn : 257.7591247558594
Eval_AverageEpLen : 173.16666666666666
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.06114453449845314
Train_EnvstepsSoFar : 0
TimeSinceStart : 3.8390719890594482
Initial_DataCollection_AverageReturn : 5383.310325177668
```
### the amount of training data per iteration:

```bash
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--train_batch_size 500
```

```
Eval_AverageReturn : 1070.5927734375
Eval_StdReturn : 1467.325439453125
Eval_MaxReturn : 3612.020751953125
Eval_MinReturn : 208.27178955078125
Eval_AverageEpLen : 259.25
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.043847132474184036
Train_EnvstepsSoFar : 0
TimeSinceStart : 13.595988035202026
Initial_DataCollection_AverageReturn : 5383.310325177668
```

```bash
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--train_batch_size 1000 
```

```
Eval_AverageReturn : 1073.7362060546875
Eval_StdReturn : 1408.5751953125
Eval_MaxReturn : 3511.910888671875
Eval_MinReturn : 193.8118438720703
Eval_AverageEpLen : 258.5
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.04294000193476677
Train_EnvstepsSoFar : 0
TimeSinceStart : 4.536325693130493
Initial_DataCollection_AverageReturn : 5383.310325177668
```

```bash
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--train_batch_size 3000 
--batch_size 5000
```

```
Eval_AverageReturn : 2706.299560546875
Eval_StdReturn : 2515.970947265625
Eval_MaxReturn : 5222.2705078125
Eval_MinReturn : 190.32859802246094
Eval_AverageEpLen : 543.0
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.04013544321060181
Train_EnvstepsSoFar : 0
TimeSinceStart : 4.580475330352783
Initial_DataCollection_AverageReturn : 5383.310325177668
```

```bash
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 1 
--expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--train_batch_size 5000 
--batch_size 10000
```

```
Eval_AverageReturn : 2706.299560546875
Eval_StdReturn : 2515.970947265625
Eval_MaxReturn : 5222.2705078125
Eval_MinReturn : 190.32859802246094
Eval_AverageEpLen : 543.0
Train_AverageReturn : 5383.310325177668
Train_StdReturn : 54.15251563871789
Train_MaxReturn : 5437.462840816386
Train_MinReturn : 5329.1578095389505
Train_AverageEpLen : 1000.0
Training Loss : 0.04013544321060181
Train_EnvstepsSoFar : 0
TimeSinceStart : 4.495886325836182
Initial_DataCollection_AverageReturn : 5383.310325177668
```



First, the training does not converge when `num_agent_train_steps_per_iter=1000`.

When we increase the training steps, the policy improves a lot.

Second, the result shows that `train_batch_size=100` training data is not enough to train a good policy.

As we increase the train_batch_size, and the size of expert data set, the policy improves some until it hit bottleneck(train_batch_size=3000 ,batch_size=5000).

But simply just adding more expert data, the policy does not improve due to insufficient steps for convergence and lack of training data.
## 4 DAGGER
```shell
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Ant.pkl 
--env_name Ant-v4 --exp_name dagger_ant --n_iter 10 
--do_dagger --expert_data cs285/expert_data/expert_data_Ant-v4.pkl 
--video_log_freq -1
```

```
Eval_AverageReturn : 4853.2392578125
Eval_StdReturn : 0.0
Eval_MaxReturn : 4853.2392578125
Eval_MinReturn : 4853.2392578125
Eval_AverageEpLen : 1000.0
Train_AverageReturn : 4798.09228515625
Train_StdReturn : 0.0
Train_MaxReturn : 4798.09228515625
Train_MinReturn : 4798.09228515625
Train_AverageEpLen : 1000.0
Training Loss : 0.0006353934877552092
Train_EnvstepsSoFar : 9000
TimeSinceStart : 14.217190265655518
```

```bash
python cs285/scripts/run_hw1.py 
--expert_policy_file cs285/policies/experts/Walker2d.pkl 
--env_name Walker2d-v4 --exp_name bc_Walker2d --n_iter 10 
--do_dagger --expert_data cs285/expert_data/expert_data_Walker2d-v4.pkl 
--video_log_freq -1
```

```
Eval_AverageReturn : 5198.92041015625
Eval_StdReturn : 0.0
Eval_MaxReturn : 5198.92041015625
Eval_MinReturn : 5198.92041015625
Eval_AverageEpLen : 1000.0
Train_AverageReturn : 5473.08837890625
Train_StdReturn : 0.0
Train_MaxReturn : 5473.08837890625
Train_MinReturn : 5473.08837890625
Train_AverageEpLen : 1000.0
Training Loss : 0.012517629191279411
Train_EnvstepsSoFar : 9078
TimeSinceStart : 12.509217023849487
```

