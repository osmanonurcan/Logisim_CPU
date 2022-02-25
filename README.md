# Logisim_CPU

## Projede Yapılanlar 

Program Counter, Instruction Memory, Registers, ALU, Memory birimlerinin tasarımları yapılarak SUB, OR, STORE işlemleri yapılmıştır.

Program Counter: Her clock sinyalinde adresi 2 byte ilerletir.

Instruction Memory: PC’den aldığı adres ile komut gönderir. Komut splitter yardımıyla 7 bit Opcode, 3’er bit Rm, Rn, Rd olmak üzere 4’ ayrılır.
- Opcode: Yine bir splitter yardımıyla 2 bit Selector, 1 bit MemWrite, 1 bit MemtoReg olarak ayrılır.  

Registers: 8 adet 16 bit register’lar kullanılmıştır. 8 adet register olduğu için decoder’a 3 bit verilerek register seçimi yapılmaktadır. Seçilen register’a data yazılılabilir. 2 adet Multiplexer ile 2 register’dan data okunur ve ALU birimine gönderilir.

ALU: Opcode’dan gelen Selector bitleri ve 2 adet Multiplexer yardımıyla ADD, SUB, AND, OR seçimi yapılır.
- ADD/SUB: 16 adet 1-bir adder birimleri xor kapıları kullanılmıştır. Selector’den gelen ilk bit 1 ise SUB, 0 ise ADD işlemi yapılır.

Memory: ALU’dan gelen adres ve Registers’dan gelen data input olarak alınır. MemWrite 1 ise Registers’dan gelen data ALU’dan gelen adrese yazılır. MemRead 1 ise ALU’dan gelen adresteki data okunur. Multiplexer yardımıyla MemtoReg 1 ise Memory’den okunan data, 0 ise ALU’dan gelen adres Registers birimine gönderilir.
