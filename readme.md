# 机器人走猫步教学

## 1. 环境搭建安装
根据 README_origin.md  进行安装

## 2. 数据准备与查看
从GMR那边转到beyondmimic：  
```
python scripts/csv_to_npz_local.py --input_file  /home/ubuntu/projects/whole_body_tracking/motion_data_pkl/maobu_g1.csv --input_fps 30 --output_name maobu   --output_dir ./motions
```

查看数据：
python scripts/replay_npz_local.py --motion_file ./motions/maobu.npz


## 3. 训练策略
```
python scripts/rsl_rl/train_local.py \
  --task Tracking-Flat-G1-v0 \
  --motion_file ./motions/maobu.npz \
  --num_envs 4096 
```

## 4. 测试策略
```
python scripts/rsl_rl/play_local.py --local_wandb_path /home/ubuntu/projects/whole_body_tracking/logs/rsl_rl/g1_flat/2025-11-11_09-26-29  --task=Tracking-Flat-G1-v0 --motion_file /home/ubuntu/projects/whole_body_tracking/motions/maobu.npz --video
```

