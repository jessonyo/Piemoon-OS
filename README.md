# 🔗 Tugas Besar Milestone 1 Sistem Operasi (IF-2230) 🔗

## 🔑 Cara kerja interrupt dalam sistem operasi

  Di dalam Bios, terdapat sebuah set fungsi yang dapat memberikan arahan pada CPU. Salah satu cara dalam mengakses fitur Bios adalah melalui interrupts. Pada sistem operasi kelompok kami, kami menggunakan sebuah tabel dari vektor interrupt yang mengandung alamat segment dari handlers interrupt. Nomor dari interrupt yang digunakan adalah indeks dari tabel tersebut, seperti contohnya INT 10h, yang merupakan indeks yang sering digunakan dalam program ini karena vektor ini mempersiapkan handler interrupt dengan tipe real mode yang memberikan servis grafis dan video, output karakter dan string, sekaligus grafik secara primitif (membaca dan menulis pixel dalam mode grafik). Pada sistem OS kami, interrupt dipanggil dengan fungsi interrupt yang menerima 5 parameter, yaitu number yang mengacu pada indeks pada vektor interrupt, dan parameter AX, BX, CX, DX yang akan disesuaikan pada kebutuhan fungsi interrupt yang akan dipanggil.


## 🔑Cara kerja file kernel.asm

  Pada kernel.asm, terdapat beberapa fungsi yang berguna dalam program OS kami, yang pertama adalah putInMemory yaitu fungsi dengan parameter segment, address, dan karakter yang berguna dalam  menulis sebuah karakter pada segment memori dengan offset tertentu. Fungsi kedua adalah interrupt yang telah dijelaskan sebelumnya, lalu terdapat fungsi makeInterrupt21 yang berguna dalam mempersiapkan tabel interrupt vector, dan yang akan memanggil kode kami saat interrupt 0x21 terpanggil. Yang terakhir adalah fungsi handlInterrupt21 yang juga akan terpanggil saat terjadi interrupt pada nomor 0x21, fungsinya adalah untuk mengetes parameter AX lalu dicocokan dengan berbagai cases, jika cocok maka akan dijalankan block statement yang ada didalamnya. Pada baris terakhir di kernel.asm terdapat _imageFile : incbin "paimon.bin", incbin disini merupakan salah satu syntax assembly yang memberikan pengarahan untuk meng-include sebuah file dalam file yang sedang di assemble. File yang diinclude ini akan dimasukkan dan digunakan nantinya tanpa di assemble. "paimon.bin" disini adalah nama file yang akan di-include dalam assembly dan file ini akan dipergunakan untuk mengambar boot logo dalam mode grafis.  

## 🔑Perintah yang tersedia
  ● mv (memindahkan file/folder)
    mv <sourcefile> <targetfolder/targetfilepath>
  ● cp (mengcopy file/folder)
    cp <>
  ● mkdir (membuat directory)
    mkdir <foldername>
  ● rm (menghapus file/folder)
    rm -r <foldername> atau rm <foldername/filename>
    -r digunakan untuk folder yang tidak kosong
  ● cat (mencetak isi file)
    cat <filepath>
  ● ln (membuat symbolic link)
    ln <sourcefilepath> <targetfilepath> atau ln -s <sourcefilepath> <targetfilepath>