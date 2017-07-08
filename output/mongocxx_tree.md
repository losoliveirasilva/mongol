```
C:.
├───bin
│       libbsoncxx.dll
│       libmongocxx.dll
│
├───include
│   ├───bsoncxx
│   │   └───v_noabi
│   │       └───bsoncxx
│   │           │   decimal128.hpp
│   │           │   json.hpp
│   │           │   oid.hpp
│   │           │   types.hpp
│   │           │   validate.hpp
│   │           │   view_or_value.hpp
│   │           │
│   │           ├───array
│   │           │       element.hpp
│   │           │       value.hpp
│   │           │       view.hpp
│   │           │       view_or_value.hpp
│   │           │
│   │           ├───builder
│   │           │   │   concatenate.hpp
│   │           │   │   core.hpp
│   │           │   │
│   │           │   ├───basic
│   │           │   │       array.hpp
│   │           │   │       document.hpp
│   │           │   │       helpers.hpp
│   │           │   │       impl.hpp
│   │           │   │       kvp.hpp
│   │           │   │       sub_array.hpp
│   │           │   │       sub_document.hpp
│   │           │   │
│   │           │   └───stream
│   │           │           array.hpp
│   │           │           array_context.hpp
│   │           │           closed_context.hpp
│   │           │           document.hpp
│   │           │           helpers.hpp
│   │           │           key_context.hpp
│   │           │           single_context.hpp
│   │           │           value_context.hpp
│   │           │
│   │           ├───cmake
│   │           ├───config
│   │           │   │   compiler.hpp
│   │           │   │   config.hpp
│   │           │   │   export.hpp
│   │           │   │   postlude.hpp
│   │           │   │   prelude.hpp
│   │           │   │   version.hpp
│   │           │   │
│   │           │   └───private
│   │           ├───document
│   │           │       element.hpp
│   │           │       value.hpp
│   │           │       view.hpp
│   │           │       view_or_value.hpp
│   │           │
│   │           ├───enums
│   │           │       binary_sub_type.hpp
│   │           │       type.hpp
│   │           │
│   │           ├───exception
│   │           │       error_code.hpp
│   │           │       exception.hpp
│   │           │
│   │           ├───private
│   │           ├───stdx
│   │           │       make_unique.hpp
│   │           │       optional.hpp
│   │           │       string_view.hpp
│   │           │
│   │           ├───string
│   │           │       view_or_value.hpp
│   │           │
│   │           ├───test
│   │           ├───third_party
│   │           │   └───mnmlstc
│   │           │       ├───core
│   │           │       │       algorithm.hpp
│   │           │       │       algorithm.hpp.bak
│   │           │       │       any.hpp
│   │           │       │       any.hpp.bak
│   │           │       │       functional.hpp
│   │           │       │       functional.hpp.bak
│   │           │       │       iterator.hpp
│   │           │       │       iterator.hpp.bak
│   │           │       │       memory.hpp
│   │           │       │       memory.hpp.bak
│   │           │       │       numeric.hpp
│   │           │       │       numeric.hpp.bak
│   │           │       │       optional.hpp
│   │           │       │       optional.hpp.bak
│   │           │       │       range.hpp
│   │           │       │       range.hpp.bak
│   │           │       │       string.hpp
│   │           │       │       string.hpp.bak
│   │           │       │       type_traits.hpp
│   │           │       │       type_traits.hpp.bak
│   │           │       │       utility.hpp
│   │           │       │       utility.hpp.bak
│   │           │       │       variant.hpp
│   │           │       │       variant.hpp.bak
│   │           │       │
│   │           │       └───share
│   │           │           └───cmake
│   │           │               └───core
│   │           │                       core-config-version.cmake
│   │           │                       core-config-version.cmake.bak
│   │           │                       core-config.cmake
│   │           │                       core-config.cmake.bak
│   │           │
│   │           ├───types
│   │           │       value.hpp
│   │           │
│   │           └───util
│   │                   functor.hpp
│   │
│   └───mongocxx
│       └───v_noabi
│           └───mongocxx
│               │   bulk_write.hpp
│               │   client.hpp
│               │   collection.hpp
│               │   cursor.hpp
│               │   database.hpp
│               │   hint.hpp
│               │   insert_many_builder.hpp
│               │   instance.hpp
│               │   logger.hpp
│               │   pipeline.hpp
│               │   pool.hpp
│               │   read_concern.hpp
│               │   read_preference.hpp
│               │   stdx.hpp
│               │   uri.hpp
│               │   validation_criteria.hpp
│               │   write_concern.hpp
│               │   write_type.hpp
│               │
│               ├───cmake
│               ├───config
│               │   │   compiler.hpp
│               │   │   config.hpp
│               │   │   export.hpp
│               │   │   postlude.hpp
│               │   │   prelude.hpp
│               │   │   version.hpp
│               │   │
│               │   └───private
│               ├───exception
│               │   │   authentication_exception.hpp
│               │   │   bulk_write_exception.hpp
│               │   │   error_code.hpp
│               │   │   exception.hpp
│               │   │   logic_error.hpp
│               │   │   operation_exception.hpp
│               │   │   query_exception.hpp
│               │   │   server_error_code.hpp
│               │   │   write_exception.hpp
│               │   │
│               │   └───private
│               ├───model
│               │       delete_many.hpp
│               │       delete_one.hpp
│               │       insert_one.hpp
│               │       replace_one.hpp
│               │       update_many.hpp
│               │       update_one.hpp
│               │       write.hpp
│               │
│               ├───options
│               │   │   aggregate.hpp
│               │   │   bulk_write.hpp
│               │   │   client.hpp
│               │   │   count.hpp
│               │   │   create_collection.hpp
│               │   │   create_view.hpp
│               │   │   delete.hpp
│               │   │   distinct.hpp
│               │   │   find.hpp
│               │   │   find_one_and_delete.hpp
│               │   │   find_one_and_replace.hpp
│               │   │   find_one_and_update.hpp
│               │   │   find_one_common_options.hpp
│               │   │   index.hpp
│               │   │   insert.hpp
│               │   │   modify_collection.hpp
│               │   │   pool.hpp
│               │   │   ssl.hpp
│               │   │   update.hpp
│               │   │
│               │   └───private
│               ├───private
│               ├───result
│               │       bulk_write.hpp
│               │       delete.hpp
│               │       insert_many.hpp
│               │       insert_one.hpp
│               │       replace_one.hpp
│               │       update.hpp
│               │
│               ├───test
│               │   ├───model
│               │   ├───options
│               │   │   └───private
│               │   ├───private
│               │   └───result
│               └───test_util
└───lib
    │   libbsoncxx.a
    │   libbsoncxx.dll.a
    │   libmongocxx.a
    │   libmongocxx.dll.a
    │
    ├───cmake
    │   ├───libbsoncxx-3.1.1
    │   │       libbsoncxx-config-version.cmake
    │   │       libbsoncxx-config.cmake
    │   │
    │   └───libmongocxx-3.1.1
    │           libmongocxx-config-version.cmake
    │           libmongocxx-config.cmake
    │
    └───pkgconfig
            libbsoncxx.pc
            libmongocxx.pc
```
