# Either

[![test](https://github.com/jechol/either/actions/workflows/test.yml/badge.svg)](https://github.com/jechol/either/actions/workflows/test.yml)
[![Coverage Status](https://coveralls.io/repos/github/jechol/either/badge.svg?branch=main)](https://coveralls.io/github/jechol/either?branch=main)
[![Hex.pm](https://img.shields.io/hexpm/v/either)](https://hex.pm/packages/either)
[![GitHub](https://img.shields.io/github/license/jechol/either)](https://github.com/jechol/either/blob/main/LICENSE)

`Either` is helpers to handle `:ok`, `{:ok, value}`, `:error` and `{:error, reason}` in consistent way.

This library is copied from `Reather.Either` from [SeokminHong/reather-lite](https://github.com/SeokminHong/reather-lite).

## Installation

```elixir
def deps do
  [
    {:either, "~> 0.1.1"}
  ]
end
```

## Usage

### `Either.new`

Convert a value into `ok` or `error` tuple. The result is a tuple having
an `:ok` or `:error` atom for the first element, and a value for the second
element.

### `Either.error`

Make an error tuple from a value.

### `Either.map`

`map` a function to an either tuple.
The given function will be applied lazily
when the either is an `ok` tuple.

### `Either.traverse`

Transform a list of eithers to an either of a list.
If any of the eithers is `error`, the result is `error`.

```elixir
iex> [{:ok, 1}, {:ok, 2}] |> Either.traverse()
{:ok, [1, 2]}
iex> [{:ok, 1}, {:error, "error!"}, {:ok, 2}]
...> |> Either.traverse()
{:error, "error!"}
```

## LICENSE

[MIT](./LICENSE)
