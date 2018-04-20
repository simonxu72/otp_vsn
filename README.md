# [otp_vsn](https://github.com/fenollp/otp_vsn) [![CircleCI](https://circleci.com/gh/fenollp/otp_vsn/tree/master.svg?style=svg)](https://circleci.com/gh/fenollp/otp_vsn/tree/master) [![TravisCI build status](https://travis-ci.org/fenollp/otp_vsn.svg?branch=master)](https://travis-ci.org/fenollp/otp_vsn)

Macros defined per Erlang/OTP version so you don't have to.

This saves you the copy/pasting/tweaking of [`erl_opts`'s `platform_define`](https://www.rebar3.org/docs/configuration#section-compilation).

Header-only, no dependencies. Supports releases from `R16B01` to latest.

Note: no need to include `otp_vsn` in your apps or releases. This should only be a compile-time dependency!

```erlang
{deps, [{otp_vsn, "~>1.0"}]}.
```

```erlang
...
-include_lib("otp_vsn/include/otp_vsn.hrl").
...
-ifdef(OTP_19_AND_ABOVE).
...
-endif.
...
```

## Macros

* `OTP_VSN`: OTP version string in `MAJOR.MINOR.PATCH` format
    * Zeros are added where needed (e.g. `"16.1.0"` for R16B01)
* `OTP_VSN_MAJOR`: above `MAJOR` part as an integer
* `OTP_VSN_MINOR`: above `MINOR` part as an integer
* `OTP_VSN_PATCH`: above `PATCH` part as an integer
* `OTP_VSN_MAJOR_STRING`: `?OTP_VSN_MAJOR` as a string
* `OTP_VSN_MINOR_STRING`: `?OTP_VSN_MINOR` as a string
* `OTP_VSN_PATCH_STRING`: `?OTP_VSN_PATCH` as a string
* `OTP_{{MAJOR}}_AND_ABOVE`: defined & set to `true` for `?OTP_VSN` `MAJOR.0.0` and all version after that
    * e.g. for OTP 19.0 `?OTP_19_AND_ABOVE = true` but on OTP 18.3 it is not defined
* `OTP_{{MAJOR}}_AND_BELOW`: defined & set to `true` for `?OTP_VSN` `MAJOR._._` and all versions before that
    * e.g. for OTP 19.0 `?OTP_19_AND_BELOW = true` but on OTP 20.0 it is not defined
* `OTP_VSN_HAS_MAPS`: defined for releases which have maps (all since OTP 17.0)

If you'd like to see more macros you are welcome to
* open an issue at https://github.com/fenollp/otp_vsn/issues
* open a pull request at https://github.com/fenollp/otp_vsn/pulls
