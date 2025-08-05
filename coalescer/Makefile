GENCODE_SM50 := -gencode=arch=compute_50,code=\"sm_50,compute_50\"
GENCODE_SM80 := -gencode=arch=compute_80,code=\"sm_80,compute_80\"
GENCODE_SM90 := -gencode=arch=compute_90,code=\"sm_90,compute_90\"

CUOPTS =   $(GENCODE_SM90)  $(GENCODE_SM80)  


CC := nvcc

INCLUDE := 
LIB := 

SRC = l1_stride.cu

EXE = l1_stride

NVCC_FLGAS = -Xptxas -dlcm=ca

release:
	$(CC) $(NVCC_FLGAS) $(CUOPTS) $(SRC) -o $(EXE) -I$(INCLUDE) -L$(LIB) -lcudart

clean:
	rm -f *.o; rm -f $(EXE)

run:
	./$(EXE)

profile:
	nvprof ./$(EXE)

events:
	nvprof  --events elapsed_cycles_sm ./$(EXE)

profileall:
	nvprof --concurrent-kernels off --print-gpu-trace -u us --metrics all --demangling off --csv --log-file data.csv ./$(EXE)

