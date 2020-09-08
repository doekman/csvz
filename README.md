# csvz

`csvz` is the hot new open database standard that is taking the entire technological world by storm.

A `csvz` file is literally just a bunch of `csv` files, in a zip file, that has been renamed to have a ".csvz" file extension.

-----

> Are you using `csvz` ? Why not? `csvz` is the amazing new technology that brings together the worlds of data science, sql and no-sql. Is it no-sql's answer to the rdbms? Or is it the rdbms answer to no-sql? You decide.

-----

**Contents**

  - [The csvz specification](#the-csvz-specification)
    - [`csvz-0` A csvz file is literally just a bunch of `csv` files, in a zip file with a file name that ends with ".csvz"](#`csvz-0`-a-csvz-file-is-literally-just-a-bunch-of-`csv`-files-in-a-zip-file-with-a-file-name-that-ends-with-".csvz")
    - [`csvz-meta-files` A csvz file can contain a file called `files.csv` describing the contents of the file](#`csvz-meta-files`-a-csvz-file-can-contain-a-file-called-`files.csv`-describing-the-contents-of-the-file)
    - [`csvz-meta-columns` A csvz file can contain a file called `filecolumns.csv`](#`csvz-meta-columns`-a-csvz-file-can-contain-a-file-called-`filecolumns.csv`)
    - [`csvz-meta-relations` A csvz file can contain a file called `relationships.csv`](#`csvz-meta-relations`-a-csvz-file-can-contain-a-file-called-`relationships.csv`)
  - [A list of `csvz-compliant` Tools and Libraries](#a-list-of-`csvz-compliant`-tools-and-libraries)
  - [Contribute](#contribute)
  - [License](#license)

## The csvz specification

The `csvz` specification has several simple fragments

The `csvz` specification is broken into meaningful fragments. Tools can call them `csvz-compliant` if they only cater for the first fragment of the specification. They can also indicate other fragments of the specification that they have implemented.

### `csvz-0` A csvz file is literally just a bunch of `csv` files, in a zip file with a file name that ends with ".csvz"

A csvz file is compliant with `csvz-0` if it is literally just a bunch of `csv` files, in a zip file, that has been renamed to have a ".csvz" file extension.

The `csv` files themselves should comply with [`RFC 4180`](https://github.com/secretGeek/AwesomeCSV#standards).

(Anywhere that this spec refers to "a csv file" it means a file that complies with `RFC 4180`.) (at the very least).

(Anywhere that `the csvz specification` refers to "this spec" it means `the csvz specification`.)


### `csvz-meta-files` A csvz file can contain a file called `files.csv` describing the contents of the file

If present, the file `files.csv` contains metadata about all of the files included in the `csvz` file.

(The file `files.csv` is a csv file.)

(Anywhere that this spec refers to a file with a name that ends with ".csv" it means the file is a csv file, as described in `csvz-0`.)


`Files.csv` meets the following description:


- There is a header row naming the columns in this file
- Each data row describes a different file
- The columns must include a column called "filename" 
- There may be more columns. Some suggestions (not required for this specification)
    - `Bytes` - the size of the file in bytes
    - `Rows` - the number of rows in the file
    - `Columns` - the number of columns in the file
    - `Description` - a description of the file
    - `Published` - the date the data in the file was first published
    - `Source` - information about the source of the data in the file
- 

(The word "must" is used for parts of the specification that are required for a file or tool to claim compliance with the standards described in this spec. The word "may" is used for parts which are not required; Optional sections may be covered in more detail, as required elements in a subsequent fragment of this spec.)

### `csvz-meta-columns` A csvz file can contain a file called `filecolumns.csv`

If present, the file `filecolumns.csv` contains metadata about all of the columns in all of the files included in the `csvz` file.

`filecolumns.csv` meets the following description:


- There is a header row naming the columns in this file
- Each data row describes a different column in a different file
- The columns must include a column called "filename" and a column called "column".
- It is expected that the columns "filename" and "column" are unique.
    - If the columns "filename" and "column" are not unique, then any meta data about that file may not be correctly interpreted. This may cause difficulties
- There should be more columns than just the "filename" and "column" column. Some suggestions:
    - `type` - the type of the column. (Types are not described in this spec fragment)
    - `nullable` - a value indicating if the column can be null
    - `maxLength` - a nullable column, that describes the maximum length of the column, in cases where the type supports a maximum length
    - `unique` - a true/false value indicating if the values in the column should be unique
    - `primarykey` - a true/false value indicating if the column can serve as (part or whole of) the primary key of the table.
    - `description` - a description of the column
    - `units` - a nullable name description of the unit of measure
    - `published` - the date the data in the file was first published
    - `source` - information about the source of the data in the file
 
(The word "should" is used for parts of the specification that are not required, but which will lead to difficulty for users of the data or the tools if they are not commplied with.)

### `csvz-meta-relations` A csvz file can contain a file called `relationships.csv`

If present, the file `relationships.csv` contains metadata about all of the relationships between any of the columns in any of the files in the `csvz` file.





## A list of `csvz-compliant` Tools and Libraries

The following tools and libraries are able to read, write or process `.csvz` files.

| Tool Name | Written in | Description                                                                                          |
|===========|============|======================================================================================================|
|           |            | - Packs a set of csv files into a new csvz file, and generates a `files.csv` and `filecolumns.csv`   |
|           |            | - Converts a `.csvz` file into a `.xlsx` file, that can be opened by Excel.                          |
|           |            | - Converts a `.xlsx` file into a `.csvx` file (note that not all of Excel's features are respected.) |
|           |            | - Exports a `sqlite` database into a new `.csvx` file                                                |
|           |            | - Creates a new `sqlite` database from a `.csvx` file                                                |
|           |            | - Exports a `mysql` database into a new `.csvx` file                                                 |
|           |            | - Creates a new `PostgreSQL` database from a `.csvx` file                                            |
|           |            | - Exports a `PostgreSQL` database into a new `.csvx` file                                            |
|           |            |                                                                                                      |


Note that there are currently no `csvz` compliant tools or libraries listed in this table. 

If you are aware of one, or you have created one (hint hint), a pull request is welcome.

-----

## Contribute

To experience the fun of contributing, see [Contributing](contributing.md)

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Leon Bambrick](http://secretgeek.net) has waived all copyright and related or neighboring rights to this work.
