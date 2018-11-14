# utl-export-jsonlines-newline-delimited-json-records-streamout
Export jsonlines newline delimited json records streamout.

    Export jsonlines newline delimited json records streamout

    SAS/IML/R

    github
    https://tinyurl.com/yaz29nwt
    https://github.com/rogerjdeangelis/utl-export-jsonlines-newline-delimited-json-records-streamout

    SAS Forum
    https://tinyurl.com/y82adr9m
    https://communities.sas.com/t5/SAS-Procedures/Proc-Json-to-create-newline-delimited-JSON-JSONL/m-p/512716

    macros
    https://tinyurl.com/y9nfugth
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories


    INPUT
    =====

    SD1.HAVE total obs=19

     NAME       SEX    AGE    HEIGHT    WEIGHT

     Alfred      M      14     69.0      112.5
     Alice       F      13     56.5       84.0
     Barbara     F      13     65.3       98.0
     Carol       F      14     62.8      102.5
     Henry       M      14     63.5      102.5
     James       M      12     57.3       83.0
     Jane        F      12     59.8       84.5
     Janet       F      15     62.5      112.5
     Jeffrey     M      13     62.5       84.0
     John        M      12     59.0       99.5
     Joyce       F      11     51.3       50.5
     Judy        F      14     64.3       90.0
     Louise      F      12     56.3       77.0
     Mary        F      15     66.5      112.0
     Philip      M      16     72.0      150.0
     Robert      M      12     64.8      128.0
     Ronald      M      15     67.0      133.0
     Thomas      M      11     57.5       85.0
     William     M      15     66.5      112.0


    EXAMPLE OUTPUT (not typical JSON - one record files)
    -----------------------------------------------------

    {"NAME":"Alfred","SEX":"M","AGE":14,"HEIGHT":69,"WEIGHT":112.5}
    {"NAME":"Alice","SEX":"F","AGE":13,"HEIGHT":56.5,"WEIGHT":84}
    {"NAME":"Barbara","SEX":"F","AGE":13,"HEIGHT":65.3,"WEIGHT":98}
    {"NAME":"Carol","SEX":"F","AGE":14,"HEIGHT":62.8,"WEIGHT":102.5}
    {"NAME":"Henry","SEX":"M","AGE":14,"HEIGHT":63.5,"WEIGHT":102.5}
    {"NAME":"James","SEX":"M","AGE":12,"HEIGHT":57.3,"WEIGHT":83}
    {"NAME":"Jane","SEX":"F","AGE":12,"HEIGHT":59.8,"WEIGHT":84.5}
    {"NAME":"Janet","SEX":"F","AGE":15,"HEIGHT":62.5,"WEIGHT":112.5}
    {"NAME":"Jeffrey","SEX":"M","AGE":13,"HEIGHT":62.5,"WEIGHT":84}
    {"NAME":"John","SEX":"M","AGE":12,"HEIGHT":59,"WEIGHT":99.5}
    {"NAME":"Joyce","SEX":"F","AGE":11,"HEIGHT":51.3,"WEIGHT":50.5}
    {"NAME":"Judy","SEX":"F","AGE":14,"HEIGHT":64.3,"WEIGHT":90}
    {"NAME":"Louise","SEX":"F","AGE":12,"HEIGHT":56.3,"WEIGHT":77}
    {"NAME":"Mary","SEX":"F","AGE":15,"HEIGHT":66.5,"WEIGHT":112}
    {"NAME":"Philip","SEX":"M","AGE":16,"HEIGHT":72,"WEIGHT":150}
    {"NAME":"Robert","SEX":"M","AGE":12,"HEIGHT":64.8,"WEIGHT":128}
    {"NAME":"Ronald","SEX":"M","AGE":15,"HEIGHT":67,"WEIGHT":133}
    {"NAME":"Thomas","SEX":"M","AGE":11,"HEIGHT":57.5,"WEIGHT":85}
    {"NAME":"William","SEX":"M","AGE":15,"HEIGHT":66.5,"WEIGHT":112}



    PROCESS
    =======

    %utl_submit_r64('
    library(haven);
    library(jsonlite);
    have<-read_sas("d:/sd1/have.sas7bdat");
    stream_out(have, file("d:/txt/streamout.json"));
    ');

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
      set sashelp.class;
    run;quit;


