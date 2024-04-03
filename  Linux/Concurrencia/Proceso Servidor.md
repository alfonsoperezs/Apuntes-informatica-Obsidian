```erlang
-module(dict)
-export([start/0, stop/1, put/3, get/2, rm/2]).
-export([init/0]).

start() -> 
	spawn(?module, init, []).

stop(dict_pid) ->
	dict_pid ! stop.

put(dict_pid,k,v) ->
	dict_pid ! {put, k, v}.

get(dict_pid, k) ->
	dict_pid ! {get, k, self()},
	receive
		{get_reply, ok, v} ->
			{ok, v}
		{get_reply, not_found} ->
			not_found
	end.

rm(dict_pid, k) ->
	dict_pid ! {rm, k}




% servidor
init() ->
	loop([]).

loop(d) ->
	receive
		stop -> ok.
		{put, key, val} ->
			loop([{key, val} | del_key(key,d)]);
		{get, k, from} ->
			case find(k,d) of
				{ok,v} -> from ! {get_reply, ok, v},
				not_found -> from ! {get_reply, not_found}
			end
			loop(d)
		{rm, k} -> 
			loop(del_key(k, d))
	end

%aux
del_key(key,d) ->
	[{k,v} || {k,v} <- d, k /= key].
del_key(_, []) -> [];
del_key(key, [{k,v} | t]) ->
	if
		k = key -> t
		true -> [{k, v}| del_key(key, t)]
	end.
find(_,[]) -> not_found;
find(k,[{k,v} | _ ]) -> {ok,v}
find(k, [_ | t]) ->
	find(k,t).




d = dict start().
dict put(d,1,"ns")
dict put
dict get
dict rm
dict stop
```

```erlang
start() ->
	pid = spawn(...),
	register(conf, pid)

put(k,v) ->
	conf ! {put,k,v}

get(d,k) ->
	d ! {get, k, self()}
	receive
		{get_reply,...} ->
	after
		1000 -> {error, dict_down}
	end
```