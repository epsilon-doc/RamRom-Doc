
# Storage

Storage is a class declared in [`ion/src/shared/storage.cpp`](https://github.com/numworks/epsilon/blob/master/ion/src/shared/storage.cpp). It is located in RAM, its purpose is to store user scripts (and KhiCAS sessions on Delta/Omega). Its address and size can be retrieved from [PlatformInfo](/Shared/Ion/PlatformInfo.md), at offset `0x14` and `0x18`.

Storage is basically a big buffer, containing some [Records](#record). It uses a magic number, `0xBADD0BEE` (big endian), called Magic.

| Offset                | Name             | Type                | Definition                               |
|-----------------------|------------------|---------------------|------------------------------------------|
|  0x00                 | m_magicHeader    | uint32_t            | Magic number, used to check integrity    |
|  0x04                 | m_buffer         | char[k_storageSize] | Huge buffer. Contains [Records](#record) |
|  0x08 + k_storageSize | m_magicFooter    | uint32_t            | Same as m_magicHeader                    |

# Record
Record is a class declared in [`ion/src/shared/storage.cpp`](https://github.com/numworks/epsilon/blob/master/ion/src/shared/storage.cpp). Records are located inside of Storage's m_buffer. Each record represents one file.

| Offset    | Name   | Type     | Definition                          |
|-----------|--------|----------|-------------------------------------|
|  0x00     | m_size | uint16_t | Size of the record, in bytes        |
|  0x02     | m_name | char[?]  | Name of the record, null-terminated |
|  0x02 + ? | m_data | uint32_t | Content, null-terminated            |

m_size is the size of m_name + the size of m_data.
Note: The way that epsilon handle's Records is that the size is used to loop trough records. The reading of the data happens with standards string fuctions, since everything is null-terminated.
