 MCHP - SPI Image generator for Carlsbad SPI image gen KHB
========================================

THIS FOLDER CONTAINS FOLLOWING FILES:
1) auto_build			 :Label inforamtion of the tool
1) Keys			 : Test ECDSA384 keys

2) Input		 : source code of the header format of the 
							EC_FW tag0/1
							
4) help.txt				 : SPI configuration and usage of the SPI IMAGE GEN 

5)SPI_config  			 : Input configuration for the 
							carlsbad_SPI_image Tool

6) 	auto_spi_img_gen.bat : batch script to genertae the spi image
							using the HEX/SPI configuration file
		Usage:
			auto_spi_img_gen.bat : batch script to genertae the spi image
									using the HEX/SPI configuration file
			auto_spi_img_gen.bat   < HEX file >    <spi_cfg.ini configuration> 

		Output of the Tool generates as follows :
			Internal Flash: spi_image.bin - EC_FW related image, KHB/TAG0/1
	
7) srec_cat.exe			: Convert the mplabx hex into BIN format of INTEL format

readme.txt  : This File

release.txt : Release notes
¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤
                                E.N.D  O.F  D.O.C.U.M.E.N.T
¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤¤