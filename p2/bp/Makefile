BP_EXEC = bp.m
BP_PRED_EXEC = bp_pred.m
DATA_DIR = ../data
OUTPUT_DIR = ../output
XOR_IN = $(DATA_DIR)/xor2.txt
XOR_OUT = $(OUTPUT_DIR)/xor2.out
PR1_IN = $(DATA_DIR)/problema_real1.txt
PR1_OUT_H1 = $(OUTPUT_DIR)/pr1h1.out
PR1_OUT_H2 = $(OUTPUT_DIR)/pr1h2.out
PR1_OUT_H3 = $(OUTPUT_DIR)/pr1h3.out
PR1_OUT_A1 = $(OUTPUT_DIR)/pr1a1.out
PR1_OUT_A2 = $(OUTPUT_DIR)/pr1a2.out
PR2_TRAIN_IN = $(DATA_DIR)/problema_real2.txt
PR2_TEST_IN = $(DATA_DIR)/problema_real2_no_etiquetados.txt
PR2_OUT = $(OUTPUT_DIR)/predicciones_nnet.txt
PR3_IN = $(DATA_DIR)/problema-real-3clases.txt
PR3_OUT_H1 = $(OUTPUT_DIR)/pr3h1.out
PR3_OUT_H2 = $(OUTPUT_DIR)/pr3h2.out
PR3_OUT_H3 = $(OUTPUT_DIR)/pr3h3.out
PR3_OUT_A1 = $(OUTPUT_DIR)/pr3a1.out
PR3_OUT_A2 = $(OUTPUT_DIR)/pr3a2.out
PR4_IN = $(DATA_DIR)/problema-real4.txt
PR4_OUT = $(OUTPUT_DIR)/pr4.out
PR4_IN_NORM = $(DATA_DIR)/problema-real4-norm.txt
PR4_OUT_NORM = $(OUTPUT_DIR)/pr4norm.out

help:
	@echo "IMPORTANT: This program requires Octave to work\n"
	@echo "Usage: make target\n"
	@echo "Targets available:"
	@echo "\t tarea2: Solves first real problem and xor problem with a multilayer perceptron."
	@echo "\t tarea3: Solves third real problem with a multilayer perceptron for several attributes values."
	@echo "\t tarea4: Solves fourth real problem with a multilayer perceptron."
	@echo "\t tarea5: Solves fourth real problem with normalized attributes using a multilayer perceptron."
	@echo "\t tarea6: Uses $(PR2_TRAIN_IN) to train a multilayer perceptron in order to solve "
	@echo "\t\t $(PR2_TEST_IN).  Writes predictions in $(PR2_OUT)"
	@echo "Outputs are generated in $(OUTPUT_DIR)."

all: tarea2 tarea3 tarea4 tarea5 tarea6

out_dir:
	@if ! [ -d ./$(OUTPUT_DIR) ]; then \
		echo "Creating output directory $(OUTPUT_DIR)" ;\
		mkdir ./$(OUTPUT_DIR) ; \
	fi

# bp.m input_file training_percentage alpha hidden_layer_n output_file
tarea2: out_dir xor pr1

pr1:
	@echo "Training for $(PR1_IN) with alpha=0.01 and 4 hidden nodes"
	./$(BP_EXEC) $(PR1_IN) 70 0.01 4 $(PR1_OUT_H1)

	@echo "Training for $(PR1_IN) with alpha=0.01 and 8 hidden nodes"
	./$(BP_EXEC) $(PR1_IN) 70 0.01 8 $(PR1_OUT_H2)

	@echo "Training for $(PR1_IN) with alpha=0.01 and 12 hidden nodes"
	./$(BP_EXEC) $(PR1_IN) 70 0.01 12 $(PR1_OUT_H3)

	@echo "Training for $(PR1_IN) with alpha=0.1 and 8 hidden nodes"
	./$(BP_EXEC) $(PR1_IN) 70 0.1 8 $(PR1_OUT_A1)

	@echo "Training for $(PR1_IN) with alpha=0.5 and 8 hidden nodes"
	./$(BP_EXEC) $(PR1_IN) 70 0.5 8 $(PR1_OUT_A2)

xor:
	@echo "Training for $(XOR_IN) with alpha=0.01 and 2 hidden nodes"
	./$(BP_EXEC) $(XOR_IN) 100 0.01 2 $(XOR_OUT) 

tarea3: out_dir
	@echo "Training for $(PR3_IN) with alpha=0.01 and 2 hidden nodes"
	./$(BP_EXEC) $(PR3_IN) 70 0.01 2 $(PR3_OUT_H1)

	@echo "Training for $(PR3_IN) with alpha=0.01 and 4 hidden nodes"
	./$(BP_EXEC) $(PR3_IN) 70 0.01 4 $(PR3_OUT_H2)

	@echo "Training for $(PR3_IN) with alpha=0.01 and 6 hidden nodes"
	./$(BP_EXEC) $(PR3_IN) 70 0.01 6 $(PR3_OUT_H3)

	@echo "Training for $(PR3_IN) with alpha=0.1 and 4 hidden nodes"
	./$(BP_EXEC) $(PR3_IN) 70 0.1 4 $(PR3_OUT_A1)

	@echo "Training for $(PR3_IN) with alpha=0.5 and 4 hidden nodes"
	./$(BP_EXEC) $(PR3_IN) 70 0.5 4 $(PR3_OUT_A2)

tarea4: out_dir
	@echo "Training for $(PR4_IN) with alpha=0.01 and 7 hidden nodes"
	./$(BP_EXEC) $(PR4_IN) 70 0.01 7 $(PR4_OUT)

tarea5: out_dir
	@echo "Training for $(PR4_IN_NORM) with alpha=0.01 and 7 hidden nodes"
	./$(BP_EXEC) $(PR4_IN_NORM) 70 0.01 7 $(PR4_OUT_NORM)

tarea6: out_dir
	@echo "Training with $(PR2_TRAIN_IN) to solve $(PR2_TEST_IN) with alpha=0.01 and 5 hidden nodes"
	./$(BP_PRED_EXEC) $(PR2_TRAIN_IN) $(PR2_TEST_IN) $(PR2_OUT) 0.01 5
