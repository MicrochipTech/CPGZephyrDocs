Usage Doc for the SPI Image generator 
=====================================
Everglades_SPI_GEN Version  3.5 2018-01-15

SPI Image Utility  usage- 
    > everglades_spi_gen.exe -i <cfg_file_name> -o <output_spi_file_name> -m <merge_file>
    
    or 
    
    > everglades_spi_gen.exe -i <cfg_file_name> -o <output_spi_file_name> 
    
    or - output file wil be default spi_image.bin
    
    > everglades_spi_gen.exe -i <cfg_file_name> 
    
    or - input config file will spi_cfg.ini and output file wil be default spi_image.bin
    
    > everglades_spi_gen.exe 

Running "everglades_spi_gen.exe" from command prompt will take 
    "spi_cfg.txt" as a default configuration file and 
    generators the output "spi_image.bin"

Other options:
==============    
    -i cfg_file_name 
        Specifies the text config file for the SPI chip & images.
        Defaults to spi_cfg.txt

    -o output_spi_file_name
        Specifies the SPI binary output file name.
        Defaults to spi_image.bin

    -m merge_file
        Read merge file as an existing SPI binary image and create FW images 
        inside it.
        No default value

        
Configuration Details:
======================        
everglades SPI Image Generator configuration file 
SPI Configuration
    [SPI]
    ;SPI Flash Image SIze in Megabits 128 =>  16MB
    SPISizeMegabits = 128
    
    ;Use this flag if Flash map is present ignore from the config file if not 
    ;applicable, default is False turned off 
    Flashmap = false / true
    
    ;if Flashmap = true then include the Flash Map address for Shared SPI interface
    ;Base address for the Second Chip Select if supported. 
    FlshmapAddr = 0x1000
    
Image Details at Tag 0
    [IMAGE "0"]
    ;Image location in the SPI Flash
    ImageLocation = <Hex value>
    
    ;SPI read frequency supported 12 16 24 48 in Mhz
    SpiFreqMHz = select any frequency from above 
    
    ; SPI Read mode configuration supported "slow" or "fast" or "dual" or "quad"
    SpiReadCommand = slow / fast / dual / quad
    
    ; SPI pin drive strength: 2, 4, 8, or 12 mA
    SpiDriveStrength = Select Drive strength from above list
    
    ; SPI pin slew rate slow(false) or fast (true)
    SpiSlewFast = false / true
    
    ; Enable Authentication of Header, FW 
    ; Generate ECDSA signature of 64-byte Header, padded FW binary + optional encryption key header,
    ; If false bytes[31:0] of the signatures contain the SHA256(object)
    UseECDSA = false / true
    
    ; This EC key pair is used to sign and verify/authenticate the FW Image Header, 
    ; FW + optional key header optional key header.
    ; EC Private Key in PEM encoded Openssl SSLeay encrypted format
    ; This key is used to sign the Header and is NOT stored in the MEC chip.
    ECDSAPrivKeyFile = Authentication Key.pem 
    ECDSAPrivKeyPassword = PASSWORD for the Private Key

    ; Header Flag for verifying Authentication enable and Disable
    ; if proper keys are programmed in efuse - this flag can enable or disable
    ; authentication. If Authentication bit is set in Efuse this is don't care
    FwAuthtic = false / true
    
    ;To Encrypt Application binary using AES-256-CBC
    FwEncrypt = false / true
    
    ; FW may be AES-256-CBC encrypted
    ; The key is auto-generated and exchanged with the ROM using a procedure 
    ; based on ECDH.
    ; An EC Public Key is used by this program to Generate the AES-256 Key/IV 
    ; and a 64-byte key header appended to the encrypted FW binary. 
    ; The corresponding EC Private key is stored in the MEC chip and is used by 
    ; ROM to re-generated the AES-256 Key & IV.
    AesGenECPubKeyFile = <Encryption Certificate file >
    
    ;Firmware Application binary image
    FwBinFile = <Application Binary file . bin>
    
    ; Offset of 0 means append to end of header. Non-zero value locates FW at ImageLocation + FWOffset
    FwOffset = 0 
    
    ;Application firmware load address in SRAM
    FwLoadAddress = <Load address in Hex>
    
    ;Zero means get entry address from offset 0x4 of input Application binary which is the reset handler address
    ;If FWEntryAddress is non-zero then use it as entry point.
    FwEntryAddress = 0 or <Entry address in Hex if known>
    