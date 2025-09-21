```mermaid
flowchart TB


subgraph SVC[1 Service & App]
SVC1[eLoran];
SVC2[Req SNR BER];
SVC3[Ops Policy];
end


subgraph BB[2 Source / Baseband]
BB1[Line Coding NRZ RZ Manch AMI];
BB2[DPCM ADPCM];
BB3[Scrambler];
end


subgraph CC[3 Channel Coding & Framing]
CC1[LDPC Turbo];
CC2[HARQ];
CC3[Interleaver];
CC4[Frame];
end


subgraph MOD[4 Mod Demod & Pulse]
MD1[8PSK QAM FSK];
MD2[OFDM CP];
MD3[RC RRC];
MD4[FTN];
MD5[FM Pre Deemph];
end


subgraph SYNC[5 Sync & Timing]
SY1[PLL CDR];
SY2[AFC];
SY3[Timing Recov];
SY4[Pilots PRACH];
end


subgraph RF[6 RF Frontend]
RF1[LNA];
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
SEL --> QM3;
