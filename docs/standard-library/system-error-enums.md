---
title: Enumerações &lt;system_error&gt;
ms.date: 11/04/2016
f1_keywords:
- system_error/std::errc
- system_error/std::io_errc
ms.assetid: b21321b7-404a-40de-8777-a85b77c6fa58
ms.openlocfilehash: d870101c80c8a1f6164e7c89dfbb452fb0a3f9a2
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246227"
---
# <a name="ltsystemerrorgt-enums"></a>Enumerações &lt;system_error&gt;

## <a name="errc"></a> errc

Fornece nomes simbólicos para todas as macros de código de erro definidas pelo Posix em `<errno.h>`.

```
class errc {
   address_family_not_supported = EAFNOSUPPORT,
   address_in_use = EADDRINUSE,
   address_not_available = EADDRNOTAVAIL,
   already_connected = EISCONN,
   argument_list_too_long = E2BIG,
   argument_out_of_domain = EDOM,
   bad_address = EFAULT,
   bad_file_descriptor = EBADF,
   bad_message = EBADMSG,
   broken_pipe = EPIPE,
   connection_aborted = ECONNABORTED,
   connection_already_in_progress = EALREADY,
   connection_refused = ECONNREFUSED,
   connection_reset = ECONNRESET,
   cross_device_link = EXDEV,
   destination_address_required = EDESTADDRREQ,
   device_or_resource_busy = EBUSY,
   directory_not_empty = ENOTEMPTY,
   executable_format_error = ENOEXEC,
   file_exists = EEXIST,
   file_too_large = EFBIG,
   filename_too_long = ENAMETOOLONG,
   function_not_supported = ENOSYS,
   host_unreachable = EHOSTUNREACH,
   identifier_removed = EIDRM,
   illegal_byte_sequence = EILSEQ,
   inappropriate_io_control_operation = ENOTTY,
   interrupted = EINTR,
   invalid_argument = EINVAL,
   invalid_seek = ESPIPE,
   io_error = EIO,
   is_a_directory = EISDIR,
   message_size = EMSGSIZE,
   network_down = ENETDOWN,
   network_reset = ENETRESET,
   network_unreachable = ENETUNREACH,
   no_buffer_space = ENOBUFS,
   no_child_process = ECHILD,
   no_link = ENOLINK,
   no_lock_available = ENOLCK,
   no_message_available = ENODATA,
   no_message = ENOMSG,
   no_protocol_option = ENOPROTOOPT,
   no_space_on_device = ENOSPC,
   no_stream_resources = ENOSR,
   no_such_device_or_address = ENXIO,
   no_such_device = ENODEV,
   no_such_file_or_directory = ENOENT,
   no_such_process = ESRCH,
   not_a_directory = ENOTDIR,
   not_a_socket = ENOTSOCK,
   not_a_stream = ENOSTR,
   not_connected = ENOTCONN,
   not_enough_memory = ENOMEM,
   not_supported = ENOTSUP,
   operation_canceled = ECANCELED,
   operation_in_progress = EINPROGRESS,
   operation_not_permitted = EPERM,
   operation_not_supported = EOPNOTSUPP,
   operation_would_block = EWOULDBLOCK,
   owner_dead = EOWNERDEAD,
   permission_denied = EACCES,
   protocol_error = EPROTO,
   protocol_not_supported = EPROTONOSUPPORT,
   read_only_file_system = EROFS,
   resource_deadlock_would_occur = EDEADLK,
   resource_unavailable_try_again = EAGAIN,
   result_out_of_range = ERANGE,
   state_not_recoverable = ENOTRECOVERABLE,
   stream_timeout = ETIME,
   text_file_busy = ETXTBSY,
   timed_out = ETIMEDOUT,
   too_many_files_open_in_system = ENFILE,
   too_many_files_open = EMFILE,
   too_many_links = EMLINK,
   too_many_synbolic_link_levels = ELOOP,
   value_too_large = EOVERFLOW,
   wrong_protocol_type = EPROTOTYPE,
};
```

### <a name="remarks"></a>Comentários

## <a name="io_errc"></a> io_errc

Fornece nomes simbólicos para as condições de erro em \<iostream>. Pode ser usado para criar objetos [error_condition](../standard-library/error-condition-class.md) a serem comparados com o valor retornado pela função [ios_base::failure](../standard-library/ios-base-class.md#failure)`code()`.

```
class io_errc {
   stream = 1
};
```

### <a name="remarks"></a>Comentários

[std::make_error_code()](../standard-library/system-error-functions.md#make_error_code) e [std::make_error_condition()](../standard-library/system-error-functions.md#make_error_condition) são sobrecarregados para essa enumeração.

`ios_base::failure` pode conter categorias de códigos de erro diferentes de `error_condition`.

### <a name="example"></a>Exemplo

```cpp
// io_errc.cpp
// cl.exe /nologo /W4 /EHsc /MTd

#include <iostream>

using namespace std;

int main()
{
    cin.exceptions(ios::failbit | ios::badbit);

    try {
        cin.rdbuf(nullptr); // throws io_errc::stream
    }
    catch (ios::failure& e) {
        cerr << "ios failure caught: ";
        if (e.code() == make_error_condition(io_errc::stream)) {
            cerr << "io_errc stream error condition" << endl;
        }
        else {
            cerr << "unmatched error condition code " << e.code() << endl;
        }
    }
}
```
