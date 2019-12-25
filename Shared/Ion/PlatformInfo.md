
# PlatformInfo

PlatformInfo is a class declared in [`ion/src/shared/platform_info.cpp`](https://github.com/numworks/epsilon/blob/master/ion/src/shared/platform_info.cpp). It is located in internal ROM, at fixed address `0x080001c4`. It contains information such as the version of epsilon and the address of the script store. It uses a magic number, `0xF00DC0DE` (big endian), called Magic.

| Offset | Name             | Type     | Definition                                               |
|--------|------------------|----------|----------------------------------------------------------|
|  0x00  | m_header         | uint32_t | Magic number, used to check integrity                    |
|  0x04  | m_version        | char[8]  | Version of epsilon, null-terminated                      |
|  0x0C  | m_patchLevel     | char[8]  | Commit ID of the build, null-terminated                  |
|  0x14  | m_storageAddress | void*    | Address of the [Storage](/Shared/Ion/Storage.md)          |
|  0x18  | m_storageSize    | size_t   | Length of the [Storage](/Shared/Ion/Storage.md), in bytes |
|  0x1C  | m_footer         | uint32_t | Same as m_header                                         |

[Omega](https://github.com/Omega-Numworks/Omega) expands the PlatformInfo a bit. It uses a second magic number, `0xDEADBEEF` (big endian), called OmegaMagic.

| Offset | Name             | Type     | Definition                                 |
|--------|------------------|----------|--------------------------------------------|
|  0x20  | m_ohm_header     | uint32_t | OmegaMagic number, used to check integrity |
|  0x24  | m_customVersion  | char[16] | Version of omega, null-terminated          |
|  0x34  | m_username       | char[16] | Custom username, null-terminated           |
|  0x44  | m_ohm_footer     | uint32_t | Same as m_ohm_header                       |

