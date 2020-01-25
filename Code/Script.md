
# Script

Script is a class declared in [`apps/code/script.h`](https://github.com/numworks/epsilon/blob/master/apps/code/script.h). It extends [Record](/Shared/Ion/Storage.md#record).

| Offset    | Name         | Type     | Definition                                       |
|-----------|--------------|----------|--------------------------------------------------|
|  0x00     | m_size       | uint16_t | Size of the record, in bytes                     |
|  0x02     | m_name       | char[?]  | Name of the record, null-terminated              |
|  0x02 + ? | m_autoImport | uint8_t  | Wether or not the script should be auto imported |
|  0x03 + ? | m_code       | char[??] | Content, null-terminated                         |

