#!name = 红果短剧・红果漫剧去广告
#!desc = 拦截穿山甲广告、播放前贴片、开屏、埋点上报与部分电商推广；保留正片、漫画图片、登录与评论。纯域名规则，无需 MITM。
#!author = Laincat（Surge 整理）
#!homepage = https://github.com/laincat/Rules
#!category = Laincat

# ============================================================
# 来源
#   主要来源（均为 MIT）：
#     https://github.com/bluee1111/egern-hongguo-adblock/blob/main/hongguo-adblock.yaml
#     https://github.com/k6nfmm7dbr-commits/hongguo-lite
#   交叉参考（未整份导入）：
#     https://github.com/QingRex/LoonKissSurge/blob/main/Surge/番茄小说去广告.sgmodule
#     https://github.com/doovvip/sublink-worker2/blob/main/surge-modules/HongGuo-Surge-Native.sgmodule
#     https://github.com/zqzess/rule_for_quantumultX/blob/master/Surge/Module/FanQieNovel.sgmodule
#     https://github.com/gitlawyercan/fanqienovel-adguardhome-rules/blob/main/fanqienovel.txt
#     https://github.com/taiji951906413/fanqie-loon
#     https://clashios.app/stoverride/lodepuly_vpn_tool/DragonRead_remove_ads
#   核对日期：2026-10-31；来源取舍详见 ../Readme.md「红果模块与来源核对」。
#
# 使用说明
#   - 可单独使用；与 Advertising.sgmodule 同用时，将本模块列在其后。
#     Advertising 的 pre-matching 优先于本模块 DIRECT，仅调整顺序不能覆盖它。
#   - 规则可能影响共用域名的其他应用，也可能影响广告奖励或解锁。
#   - 启用后检查播放、切集、封面、登录和评论；异常时停用并查看请求记录。
#   - 刻意不拦：log.snssdk.com / gurd.snssdk.com（登录与风控，拦截可能触发
#     「环境异常」）、vas / security / effect.snssdk.com（用途不明）。
#
# 规则顺序（不要随意调整）
#   1. 必要 DIRECT 例外（正片、图片、API）
#   2. REJECT：穿山甲 / 埋点 / 广告接口 / 电商 / 贴片视频 / 弹窗落地页
#   3. qznovelvod.com 兜底 DIRECT（必须在贴片视频 REJECT 之后）
# ============================================================

[Rule]

# ---------- 1. 必要例外：正片、图片和 API 优先于广告拦截 ----------
# 正片 / 听书
DOMAIN-SUFFIX,fqnovelvod.com,DIRECT
DOMAIN-WILDCARD,v*-reading-video*.qznovelvod.com,DIRECT
DOMAIN-WILDCARD,v*-reading-videocdn*.qznovelvod.com,DIRECT
DOMAIN,n98-v-readingvideo.qznovelvod.com,DIRECT
DOMAIN-WILDCARD,*-fq-tts.fqnovelvod.com,DIRECT
# 漫剧 / 小说封面
DOMAIN-WILDCARD,p*-novel*.byteimg.com,DIRECT
# 抖音商城图片与正片缩略图（须在 p*-ad-sign REJECT 之前）
DOMAIN,p3-ad-sign.byteimg.com,DIRECT
DOMAIN,p3-tt.byteimg.com,DIRECT
# 核心 API 与静态资源
DOMAIN-WILDCARD,api*-normal.fqnovel.com,DIRECT
DOMAIN-WILDCARD,api*-normal-lq.fqnovel.com,DIRECT
DOMAIN-WILDCARD,frontier*-toutiao-lq.fqnovel.com,DIRECT
DOMAIN-WILDCARD,lf*-reading.fqnovelstatic.com,DIRECT

# ---------- 2. 拦截 ----------
# 穿山甲广告请求与素材
DOMAIN-SUFFIX,pangolin-sdk-toutiao.com,REJECT
DOMAIN-SUFFIX,pangolin-sdk-toutiao1.com,REJECT
DOMAIN-SUFFIX,pangolin-sdk-toutiao-b.com,REJECT
DOMAIN-SUFFIX,pglstatp-toutiao.com,REJECT
DOMAIN-SUFFIX,pglstatp-toutiao-b.com,REJECT
# 将上游 pangolin 关键词收窄到 DSP 域名
DOMAIN-SUFFIX,pangolin-dsp-toutiao.com,REJECT
DOMAIN-SUFFIX,pangolin-dsp-toutiao-b.com,REJECT
DOMAIN-SUFFIX,pangle.io,REJECT
DOMAIN-WILDCARD,api-access.pangolin-sdk-toutiao*.com,REJECT
DOMAIN-WILDCARD,log-api.pangolin-sdk-toutiao*.com,REJECT

# 埋点 / 上报（如影响功能可注释本组）
DOMAIN,mon.toutiaocloud.net,REJECT
DOMAIN,mon.toutiaocloud.com,REJECT
DOMAIN,i.snssdk.com,REJECT
DOMAIN,i-lq.snssdk.com,REJECT
DOMAIN,is.snssdk.com,REJECT
DOMAIN,is-lq.snssdk.com,REJECT
# 对齐 hongguo-lite：任意前缀的 *-misc 一并拦截（原仅 mon*）
DOMAIN-WILDCARD,*-misc.fqnovel.com,REJECT
DOMAIN-WILDCARD,mon*-misc-lq.fqnovel.com,REJECT
# applog：裸域名与 rtlog / log 各前缀（rtlog*-applog 非 lq 版为新增）
DOMAIN,applog.fqnovel.com,REJECT
DOMAIN-WILDCARD,rtlog*-applog.fqnovel.com,REJECT
DOMAIN-WILDCARD,rtlog*-applog-lq.fqnovel.com,REJECT
# 收窄上游关键词，覆盖 log3 / log5
DOMAIN-WILDCARD,log*-applog.fqnovel.com,REJECT

# 红果 / 番茄广告接口（只匹配 ads*-normal）
DOMAIN-WILDCARD,ads*-normal.zijieapi.com,REJECT
DOMAIN-WILDCARD,ads*-normal-*.zijieapi.com,REJECT
DOMAIN-WILDCARD,ads*-normal-lq.zijieapi.com,REJECT
DOMAIN-WILDCARD,p*-ad-sign.byteimg.com,REJECT
DOMAIN-WILDCARD,p*-developer-sign.bytemaimg.com,REJECT

# 电商推广
DOMAIN-WILDCARD,ecom*-normal-lq.ecombdapi.com,REJECT
DOMAIN-WILDCARD,ec*-core-lq.ecombdapi.com,REJECT
DOMAIN-WILDCARD,isaas*-normal-lq.ecombdapi.com,REJECT

# 播放前 / 剧集间广告视频
DOMAIN-WILDCARD,v*-reading-ad.qznovelvod.com,REJECT
DOMAIN-WILDCARD,v*-bd-daily-reading-ad.qznovelvod.com,REJECT
DOMAIN-WILDCARD,v*-se-daily-reading-ad.qznovelvod.com,REJECT
DOMAIN-WILDCARD,v*-se-sjy-daily-reading-ad.qznovelvod.com,REJECT

# ---------- 3. 兜底：其余正片 / 听书 CDN（必须在广告视频拦截之后） ----------
DOMAIN-SUFFIX,qznovelvod.com,DIRECT

# ---------- 4. 广告弹窗、小游戏与落地页 ----------
DOMAIN-SUFFIX,praisewindow.ugsdk.cn,REJECT
DOMAIN,praisewindow-sinfonlinea.ugsdk.cn,REJECT
DOMAIN,zlink.ugsdk.cn,REJECT
# 广告点击跳转 / 归因（新增，来自 lodepuly 模块）
DOMAIN,dig.bdurl.net,REJECT
DOMAIN,dig.zjurl.cn,REJECT
DOMAIN-WILDCARD,minigame*-normal.zijieapi.com,REJECT
DOMAIN-WILDCARD,minigame*-normal-*.zijieapi.com,REJECT
DOMAIN-SUFFIX,chengzijianzhan.com,REJECT
