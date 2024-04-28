切换用户
sudo -i
切换至 root 用户

安装Rust
// 执行下方两条命令配置临时源(国内服务器💻)
export RUSTUP_DIST_SERVER="https://rsproxy.cn"
export RUSTUP_UPDATE_ROOT="https://rsproxy.cn/rustup"

// 安装 rust 环境
curl --proto '=https' --tlsv1.2 -sSf https://rsproxy.cn/rustup-init.sh | sh

//执行下方命令配置环境变量
. "$HOME/.cargo/env"

//配置源
vim ~/.cargo/config

//将下方配置粘贴进去并保存

[source.crates-io]
replace-with = 'rsproxy-sparse'
[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"
[source.rsproxy-sparse]
registry = "sparse+https://rsproxy.cn/index/"
[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"
[net]
git-fetch-with-cli = true


//国外服务器环境配置💻
curl https://sh.rustup.rs -sSf | sh

. "$HOME/.cargo/env"

安装Solana
// 下载程序 (国内服务器)
wget https://mirror.ghproxy.com/https://github.com/solana-labs/solana/releases/download/v1.17.28/solana-release-x86_64-unknown-linux-gnu.tar.bz2

// 解压压缩包
tar jxf solana-release-x86_64-unknown-linux-gnu.tar.bz2

// 设置环境变量(注意自己的目录)
export PATH="/root/solana-release/bin:$PATH"

// 查看是否安装成功
solana --version


//国外服务器
sh -c "$(curl -sSfL https://release.solana.com/v1.18.4/install)"

// 设置环境变量
export PATH="/root/.local/share/solana/install/active_release/bin:$PATH"

// 查看是否安装成功
solana --version


// 下载挖矿程序
git clone https://github.com/Souging/mars-cli-v1.git
// 打开程序目录
cd mars-cli-v1

cargo build --release

mine:
~/mars-cli/target/release/mars --keypair [keypair] --rpc [rpc_url] --priority-fee 1 mine --threads 4

claim:
~/mars-cli/target/release/mars --keypair [keypair] --rpc [rpc_url] --priority-fee 1 claim


查询产量
给脚本执行权限 chmod +x get.sh

然后执行此命令查询产量/root/mars-cli-v1/get.sh

归集到主号
给脚本执行权限 chmod +x claim.sh

修改claim.sh中的claim_address和rpc_url

然后执行此命令归集orz/root/mars-cli-v1/claim.sh

