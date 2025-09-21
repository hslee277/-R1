```mermaid
flowchart TB
RF2[Mixer];
RF3[LO PLL Synth];
RF4[IF Chain Double Superhet];
RF5[PA DPD];
RF6[Duplexer SAW BAW];
RF7[RF Filters LC SAW BAW Cavity];
end


subgraph ANT[7 Antenna & Array]
AN1[Gain Pattern Pol];
AN2[MIMO Beamforming];
end


subgraph CH[8 Channel & Propagation]
CH1[AWGN kTB NF];
CH2[Fading Rayleigh Rice];
CH3[Delay Spread -> Bc];
CH4[Doppler -> Tc];
CH5[FSPL Pathloss];
CH6[Fresnel Zone];
CH7[Ionosphere LUF MUF FOT];
CH8[Velocity Dispersion];
end


subgraph RX[9 Receiver & Detection]
RX1[Matched Filter];
RX2[MLSE LLR Decision];
RX3[AGC ADC DSP];
end


subgraph QMS[10 Quality & Measurement]
QM1[EVM];
QM2[BER EbN0];
QM3[ACPR ACLR];
QM4[IMD3 IP3];
QM5[Spectrum Analyzer RBW VBW];
QM6[MDS Link Margin];
end


subgraph OPS[11 Operations & Planning]
OP1[Link Budget Pt Pr FSPL];
OP2[Freq Plan];
OP3[Site Clearance];
OP4[Compliance];
end


%% Flow edges (top-level chain)
SVC --> BB;
BB --> CC;
CC --> MOD;
MOD --> SYNC;
SYNC --> RF;
RF --> ANT;
ANT --> CH;
CH --> RX;
RX --> QMS;
QMS --> OPS;


%% Cross edges (핵심 상호의존)
CH1 --> QM1;
CH1 --> QM2;
QM2 --> CC1;
MD3 --> RX1;
MD2 --> CH3;
CH5 --> OP1;
CH6 --> OP3;
AN2 --> CH;
RF5 --> QM4;
RF7 --> SEL[Selectivity];
SEL --> QM3;
end
