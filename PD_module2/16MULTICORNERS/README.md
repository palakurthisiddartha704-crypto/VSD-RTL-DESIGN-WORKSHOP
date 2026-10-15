vsduser@vsdsquadron:~/Desktop/assignment/skywater-pdk-libs-sky130_fd_sc_hd-master$ ls -1 STA_results/*.log
STA_results/sky130_fd_sc_hd__ff_100C_1v65.log
STA_results/sky130_fd_sc_hd__ff_100C_1v95.log
STA_results/sky130_fd_sc_hd__ff_n40C_1v56.log
STA_results/sky130_fd_sc_hd__ff_n40C_1v65.log
STA_results/sky130_fd_sc_hd__ff_n40C_1v76.log
STA_results/sky130_fd_sc_hd__ff_n40C_1v95.log
STA_results/sky130_fd_sc_hd__ss_100C_1v40.log
STA_results/sky130_fd_sc_hd__ss_100C_1v60.log
STA_results/sky130_fd_sc_hd__ss_n40C_1v28.log
STA_results/sky130_fd_sc_hd__ss_n40C_1v35.log
STA_results/sky130_fd_sc_hd__ss_n40C_1v40.log
STA_results/sky130_fd_sc_hd__ss_n40C_1v44.log
STA_results/sky130_fd_sc_hd__ss_n40C_1v60.log
STA_results/sky130_fd_sc_hd__ss_n40C_1v76.log
STA_results/sky130_fd_sc_hd__tt_025C_1v80.log
STA_results/sky130_fd_sc_hd__tt_100C_1v80.log
vsduser@vsdsquadron:~/Desktop/assignment/skywater-pdk-libs-sky130_fd_sc_hd-master$ for f in STA_results/*.log; do
    echo "===== $(basename "$f") ====="
    grep -E "Path Type:|slack" "$f"
done
===== sky130_fd_sc_hd__ff_100C_1v65.log =====
Path Type: min
                                        0.2491   slack (MET)
Path Type: max
                                        4.0545   slack (MET)
===== sky130_fd_sc_hd__ff_100C_1v95.log =====
Path Type: min
                                        0.1960   slack (MET)
Path Type: max
                                        5.5668   slack (MET)
===== sky130_fd_sc_hd__ff_n40C_1v56.log =====
Path Type: min
                                        0.2915   slack (MET)
Path Type: max
                                        2.2781   slack (MET)
===== sky130_fd_sc_hd__ff_n40C_1v65.log =====
Path Type: min
                                        0.2551   slack (MET)
Path Type: max
                                        3.4112   slack (MET)
===== sky130_fd_sc_hd__ff_n40C_1v76.log =====
Path Type: min
                                        0.2243   slack (MET)
Path Type: max
                                        4.4301   slack (MET)
===== sky130_fd_sc_hd__ff_n40C_1v95.log =====
Path Type: min
                                        0.1875   slack (MET)
Path Type: max
                                        5.5919   slack (MET)
===== sky130_fd_sc_hd__ss_100C_1v40.log =====
Path Type: min
                                        0.9053   slack (MET)
Path Type: max
                                      -17.1216   slack (VIOLATED)
===== sky130_fd_sc_hd__ss_100C_1v60.log =====
Path Type: min
                                        0.6420   slack (MET)
Path Type: max
                                       -7.8740   slack (VIOLATED)
===== sky130_fd_sc_hd__ss_n40C_1v28.log =====
Path Type: min
                                        1.8296   slack (MET)
Path Type: max
                                      -62.5632   slack (VIOLATED)
===== sky130_fd_sc_hd__ss_n40C_1v35.log =====
Path Type: min
                                        1.3475   slack (MET)
Path Type: max
                                      -39.6970   slack (VIOLATED)
===== sky130_fd_sc_hd__ss_n40C_1v40.log =====
Path Type: min
                                        1.1249   slack (MET)
Path Type: max
                                      -29.6937   slack (VIOLATED)
===== sky130_fd_sc_hd__ss_n40C_1v44.log =====
Path Type: min
                                        0.9909   slack (MET)
Path Type: max
                                      -23.9079   slack (VIOLATED)
===== sky130_fd_sc_hd__ss_n40C_1v60.log =====
Path Type: min
                                        0.6628   slack (MET)
Path Type: max
                                      -10.6090   slack (VIOLATED)
===== sky130_fd_sc_hd__ss_n40C_1v76.log =====
Path Type: min
                                        0.5038   slack (MET)
Path Type: max
                                       -4.3819   slack (VIOLATED)
===== sky130_fd_sc_hd__tt_025C_1v80.log =====
Path Type: min
                                        0.3096   slack (MET)
Path Type: max
                                        1.9392   slack (MET)
===== sky130_fd_sc_hd__tt_100C_1v80.log =====
Path Type: min
                                        0.3145   slack (MET)
Path Type: max
                                        2.0935   slack (MET)