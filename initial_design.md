# Keywords

| Keyword      | Usage |
| ------------ | ----- |
| and          |       |
| as           |       |
| atomic       |       |
| auto         |       |
| bitand       |       |
| bitor        |       |
| bitnot       |       |
| bool         |       |
| break        |       |
| byte         |       |
| case         |       |
| catch        |       |
| char         |       |
| char8        |       |
| char16       |       |
| char32       |       |
| class        |       |
| concept      |       |
| continue     |       |
| const        |       |
| coroutine    |       |
| default      |       |
| delete       |       |
| do           |       |
| enum         |       |
| export       |       |
| explicit     |       |
| extern       |       |
| else         |       |
| false        |       |
| final        |       |
| float32      |       |
| float64      |       |
| float128     |       |
| for          |       |
| foreach      |       |
| fragment     |       |
| friend       |       |
| if           |       |
| import       |       |
| implicit     |       |
| in           |       |
| inline       |       |
| inspect      |       |
| int4         |       |
| int8         |       |
| int16        |       |
| int32        |       |
| int64        |       |
| int128       |       |
| is           |       |
| meta         |       |
| module       |       |
| mutable      |       |
| namespace    |       |
| not          |       |
| null         |       |
| nullptr      |       |
| operator     |       |
| or           |       |
| override     |       |
| package      |       |
| ptr          |       |
| private      |       |
| protected    |       |
| public       |       |
| ref          |       |
| register     |       |
| requires     |       |
| return       |       |
| self         |       |
| switch       |       |
| synchronized |       |
| true         |       |
| try          |       |
| type         |       |
| unsafe_ptr   |       |
| uint8        |       |
| uint16       |       |
| uint32       |       |
| uint64       |       |
| uint128      |       |
| until        |       |
| using        |       |
| var          |       |
| virtual      |       |
| void         |       |
| wchar        |       |
| while        |       |

# Operator

## Common operators

| assignment | increment/decrement | arithmetic | logical  | bit operation | comparison | member access   | other                  |
| ---------- | ------------------- | ---------- | -------- | ------------- | ---------- | --------------- | ---------------------- |
| a = b      | a++                 | +a         | not a    | bitnot b      | a == b     | a[b, c, ..., z] | function call : a(...) |
| a += b     | a--                 | -a         | !a       | ~b            | a != b     | *a              |                        |
| a -= b     |                     | a + b      | a and b  | a bitand b    | a < b      | &a              |                        |
| a *= b     |                     | a - b      | a && b   | a & b         | a > b      | a->b            |                        |
| a /= b     |                     | a * b      | a or b   | a bitor b     | a <= b     | a.b             |                        |
| a %= b     |                     | a / b      | a \|\| b | a \| b        | a >= b     | a->*b           |                        |
| a &= b     |                     | a % b      |          | a << b        | a <=> b    | a.*b            |                        |
| a \|= b    |                     | a ** b     |          | a >> b        |            |                 |                        |
| a ^= b     |                     |            |          |               |            |                 |                        |
| a <<= b    |                     |            |          |               |            |                 |                        |
| a >>= b    |                     |            |          |               |            |                 |                        |

## Special operators

| Operator  | Usage           |
| --------- | --------------- |
| a as b    | Type conversion |
| a is b    | Type constraint |
| sizeof(a) | size of object  |

# Grammar definition

Module definition:

`"module <module-name> : [module-code-safety-descriptor]";`

"If" expression:

```
"if" (<boolean-testable-expression>)
    [branch-body]
"else if" (<boolean-testable-expression>)
    [branch-body]
"else"
    [branch-body]
```

"for" expression:

```
"for"([expression-1]; [expression-2]; [expression-3])
    [body]
```

"foreach" expression:

```
"foreach"([iteration-variable-definition] in [iterable-object])
    [body]
```

"while" expression:

```
"while"([boolean-testable-expression])
    [body]
```

"return" expression:

```
"return" [return-list];
```

"using" expression:

`"using" <enum|namespace|module> <name>;`

`"using" <type-alias> = <type>;`

Variable definition:

`"var" [variable-descriptor] <variable-name>: [type-or-constraint] = [initialize-value];`

`"var" [variable-descriptor] <variable-name>: [type-or-constraint] = {[list-initializer]};`

Reference definition:

`"ref" [reference-descriptor] <reference-name>: [type-or-constraint] = <object-being-referenced>;`

Safe ownership pointer definition:

`"ptr" [pointer-descriptor] <pointer-name>: [type-or-constraint] = [object-being-pointed];`

Raw pointer definition:

`"unsafe_ptr" [pointer-descriptor] <pointer-name>: [type-or-constraint] = [object-being-pointed];`

Function definition:

`[access-level] "fn" [function-descriptor] [function-name] < [template-argument-list] >( [argument-list] ): [return-type] = [function-body]`

Class definition:

`[access-level] "class" [class-descriptor] [class-name] < [template-argument-list] >( [metaclass-descriptor] ): [base-class-list] = [class-body]`

Class initialization:

`<class-name>{.<member-name> = <value>}`

`<class-name>([constructor-argument-list])`

`<class-name>([constructor-argument-list])>{.<member-name> = <value>}`

Reflection:

`^[identifier]`

Reification:

`#[typeinfo-object]`

Type conversion:

`[variable-name] "as" [type-name]`

Type constraint:

`[variable-name] "is" [type-name]`

Type inspection:

```
"inspect"([variable-name]) {
    "is" [type] -> [function-body];
}
```

Code injection:

```
-> [fragment-or-code]
```

Code fragment:

`<"[code-sequence]">`

Example:

```
module a.main : unsafe_pointer, unsafe-memory-management;

using module std.io;
metaprint = using module std.meta.io;

module public:

class main = {
    fn main(): [i32, string] = {
        print("This will appear when you running this code");
        return 0, "multiple return value";
    }
}

private fn meta compile_run(): void = {
    print("This will appear when you compiling this code");
}

module private:

fn meta interface(type T) = {
    using enum typeinfo::access_level;
    ref clazz: typeinfo = ^T;
    for(ref member : clazz) {
        if(member.get_access_level() != PUBLIC) {
            member.set_access_level(PUBLIC);
            metaprint.warning("The member of an interface class must be public: {clazz.get_display_name()}::{member.get_display_name()}");
        }
        if(member.has_implementation()) {
            member.remove_implementation();
            metaprint.warning("The member of an interface class must not have an implementation: {clazz.get_display_name()}::{member.get_display_name()}");
        }
        if(!member.is_virtual()) {
            member.make_virtual();
            metaprint.warning("The member of an interface class must be virtual: {clazz.get_display_name()}::{member.get_display_name()}");
        }
    }
}

class fragment mixin_test = {
    public var a: i32;
    public fn func(): void = {}
}

fn meta injection_test(type T) = {
    return <"fragment class = {
        ref nope: %^T.get_display_name()%;
    }">;
}

class test_interface(interface) = {
    public virtual fn awa(): auto = delete;    //ok
    private fn nope(): auto = { return 0; };    //will get warnings
    inject -> mixin_test;    //class fragment injection
    inject -> injection_test(string);
}

fn template_test<A, B is typeconcept.integral, C is typeconcept.string, D is typeconcept.enumerable or typeconcept.bool, E is _>(a): auto = {
    var const a_var: A = {};
    inspect(x) {
        :i32 -> {print("x is i32")};
        :string -> {print("x is string")};
        :_ -> {print("x is sometype")};
    }
    return ^C.get_scope().get_display_name();
}

var ti = ^a;
var b: #ti;
```

# Standard library module

todo ;)
