# X3872_MC_Production
5 TeV boost MC generation created with cmsDriver.py in 3 steps

cd X3872_MC_Gnrt/src/
scram b -j24
Start to produce MC withs cmsDriver.py command.
1-GEN,SIM 
cmsDriver.py Configuration/Generator/python/HIJINGemb_X3872_5TeV_cff.py --conditions STARTHI53_V27::All -s GEN,SIM --process HISIGNAL -n 10 --eventcontent RAWSIM --datatier GEN-SIM --relval None --filein file:E6C7EEFE-E567-E211-BFD6-00A0D1E952FC.root --scenario HeavyIons --himix --no_exec --beamspot Match5TeVCollisionPPbBoost

2-DIGI,L1,DIGI2RAW,HLT
cmsDriver.py step2_HIJINGemb_X3872_TuneZ2star_5TeV --conditions STARTHI53_V27::All -s DIGI,L1,DIGI2RAW,HLT:PIon -n -1 --eventcontent FEVTDEBUGHLT --datatier GEN-SIM-DIGI-RAW-HLTDEBUG --filein file:HIJINGemb_X3872_5TeV_cff_py_GEN_SIM.root --inputCommands 'keep *,drop *_simEcalPreshowerDigis_*_*' --himix --no_exec 

3-RAW2DIGI,L1Reco,RECO 
cmsDriver.py step3_HIJINGemb_X3872_TuneZ2star_5TeV --conditions STARTHI53_V27::All -s RAW2DIGI,L1Reco,RECO --datatier GEN-SIM-RECO --eventcontent RECOSIM -n -1 --filein file:step2_HIJINGemb_X3872_TuneZ2star_5TeV_DIGI_L1_DIGI2RAW_HLT.root --no_exec 

For more events used crab3
Check crabCOnfig.py files for each step


