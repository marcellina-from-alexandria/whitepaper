# alexandria trust tokenomics thoughts

## how donation works

My current plan is that donors will contribute to an initiative for a given file/dataset/book collection that the DAO has decided to take responsibility for storing, or contribute to the DAO proper's discretionary funds. There will be many projects that the DAO is responsible for preserving. However, it'll probably be doable to compute a marginal value for donations to a given preserve-files-forever project: it'll be a function of an estimate of disk space needed for a copy of the project, some generalized actuarial computation over risks of data loss when storing files on combinations of different systems, and the risks of loss of income to the project due to loss of interest/future need for expensive censorship avoidance tactics/investment losses.

## donor incentive alignment

Donors will probably receive some amount of inflationary DAO governance token for donation. Figuring out the distributions of tokens to donors is something I need to do, I think we should weigh high-marginal-value donations and earlier-in-the-DAO's-existence donations higher. These two categories are maybe the same thing!

This will mean that people who made public good donations and pro-DAO donations (in the past DAO's eyes) will form an increasingly powerful contingent of the future DAO's governance. Assuming that people who are altruistic in the past remain altruistic in the future, this will be good for the DAO. Note: Funds donated directly to the DAO discretionary funds should probably be considered to have a 1.0 marginal value, because they'll be allocated however the DAO wants.

## why do we need a marginal cost function?

There will be weird distributions of marginal cost versus funding- a 2MB PDF of a Harry Potter book costs cents per year to store to both Filecoin and IPFS, but people are likely to donate silly amounts towards preserving it for their grandkids. With a $100 initial donation invested with 3% average annual returns, and a small-percentage management fee taken out at some point in the system, you can have that PDF stored for basically eternity. Where do you spend the other $10k? Towards launching copies of Harry Potter Voyager-golden-record-style into space? No- you fund the 1PB cancer genomics dataset that nobody thinks to donate to, but that the DAO has decided to take responsibility for.

The DAO will therefore somehow need to periodically smear the funds across all the datasets that it's responsible for, and invest/spend said money in the interest of ensuring those files last forever.

Note: when clients donate, they are also openly expressing their preference for the preservation of a GIVEN file, so it will be important not to make decisions that compromise a client's preferences too much. Although clients already will probably get extra governance tokens for donating to high-marginal-value projects, which boosts their incentives to work alongside the DAO (by owning valuable governance tokens) and to help other people's projects (because the tokenholders can profit from all increases in donation), people want their files of choice stored. They will stop donating if the DAO diverts necessary resources from their file of choice. This has to be taken into account in the DAO's incentives- it's the most important part of the incentive structure, because the DAO takes profit from wise investment and client donations. This is what forces the tokenholders to act in alignment with the donors' will.

## how to schmear the money??

Some thoughts on how to smear the funds around:
Tokenholders need to have some standardized and automated process that they can agree on the output of, and it should involve minimal interaction/updating from real humans. We could use actuarial risk adjustments for given files and storage mechanisms to change the marginal cost functions for various possible funds allocations, and do the allocation programmatically from there. The factors that would change over time are market conditions for investing funds held by the DAO (one factor for all preservation projects assuming all funds are in same portfolio), risks of using different storage backends (one risk profile per storage backend, possibly a variable function of censorship risk), and censorship risk/loss-of-interest-related-underfunding risk (per-file).

### risk computation

Storage backend risk functions, with some variable to change them based on the censorship threat model for a given file, could probably be computed by real humans on a monthly basis, and adopted by the DAO according to a governance mechanism that only requires interaction from a small number of parties in nearly all situations. Thinking about market risk and investment strategy could be outsourced to a semi-managed DeFi thingy like Yearn, or also done periodically by real humans, similarly to storage risk.

Per-file computations for censorship risk could probably be handled with prediction markets of DAO tokenscensorship tends to happen periodically and in a very targeted manner, so this would be O(sporadic and small-constant) in terms of attention needed per stakeholder). People worried about the censorship of a given file could go lock a few tokens into a "flag high censorship risk" fund for a period for some reward...(TODO)?

Loss-of-interest-related underfunding risk could be computed by a time-weighted average of donation versus costs of upkeep of the file. This one is pretty easy to automate. We might also add some human-adjusted Lindy effect/other factor- Plato's been around for 2000 years and we aren't likely to forget about it, Scihub is widely considered to have long-term value, but a random blog or fad novel might be quickly forgotten and should have a high risk factor if the DAO decides it's worth preserving forever.

### incentives for risk computation

Tokenholders should only profit when they participate in (and act in line with) the process, and they should lose money when they don't. So it should be profitable to honestly compute and approve honestly-computed risk factors (perhaps the DAO puts out a bounty for risk factor computations, or some prediction market takes place?), whereas it should be pricey (at least in opportunity cost) to be dishonest. TODO TODO TODO

### we have the marginal value functions of allocating money to projects. now what?

Vitalik's QF paper seems possibly smart. need to figure out how to apply it. TODO

I think the S-process allocation idea is really interesting and might be a super-relevant improvement over Vitalik's QF paper for this problem??? TODO TODO TODO DETAILS

## democracy

If tokenholders' profits come from clients over time, their incentives to act pro-DAO are aligned with the incentives of clients to donate and continue donating. Clients value long-term preservation of the files they want preserved, so the DAO needs to act in order to preserve those files if they want clients to keep donating. Tokenholders could theoretically rugpull (short time-preference, looting all funds under management at the cost of all possible future funds)- this must be avoided. Their governance actions need to be future-oriented.

Aside: complex democratic operations are going to be annoying to do on-chain, so I think we should at least consider the possibility of a governance L2. All the governance could happen on some kind of sidechain protocol (probably similar to optimism) and then rectified on-chain. We could shift as much or little of contractual legwork on/off chain- swapping out valid binary hashes of "the governance binary run by some validators, who take some defined on-chain input, and whose agreed-upon output determines where we move funds" would be one extreme, and fully-on-chain-everything would be the other. One is a lot cheaper than the other.

### the price of governing

DAO governance actions will be "priced" by staking tokens in a time-locked vault. Staking reduces the user's optionality to divorce their incentives from the DAO's for some predetermined period. So long as they have staked tokens for some period, they will receive voting shares that linearly increase with the amount of DAO tokens staked and also linearly increase with the remaining staking duration (TODO FIXME, ought this actually be linear?). They will be able to redeem their governance tokens once the lockup period ends. Voting shares will decrease as remaining lockup time decreases, but participants can "bump" the voting period up to any value less than or equal to the original period at any time.

Proposals for votes to change parameters (TODO which ones?) of the system can be made by any address with greater than (TODO how much) voting shares. Proposals for votes to change the constitution of the DAO (TODO should we even do this?? what percentage vote to approve?) can be made by any address with greater than (TODO how much greater) voting shares.

### voting

Votes will be decided by whichever option has the most voting shares in favor of it. Votes will happen in periodic batches, and each voting share can be used once per batch- this allows for ranked-choice voting on groups of incentives. This mechanism does not burn votes, people keep their governance power between batches as long as they remain staked.

### reward shares

Locking (and voting!) is the only way to get DAO reward shares. Locking provides one reward share per voting share, and each vote participation gets a reward share of (TODO how much?). 

This means that people whose incentives are aligned with the protocol (by having locked tokens to get voting shares) will get payouts. People who vote will also get a little extra reward indefinitely, to ensure they stay aligned with keeping client donations flowing in after their lockup period ends.

Reward shares would probably be traded on uniswap, so buybacks from the DAO treasury to consolidate who gets dividends could also be an option. This probably would have to be an occasional vote-based thing.

### loan-based representative democracy

People can collateralized-loan out their governance tokens to whoever they want at some APY set by DeFi markets- people will only borrow the governance tokens when they think they can make a profit while paying the APY. Therefore, the APY will settle to (COMPUTE THIS, it's some marginal-looking function of labor costs in DAO governance, and expected profits of doing DAO governance with some amount of money).

People can also *delegate* their tokens out to specific parties with contractual collateralized loans for one specific person (TODO TODO TODO whole mechanics of this)