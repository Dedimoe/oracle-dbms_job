# oracle-dbms_job
oracle-dbms_job

```

--1-- submit job

SQL> VARIABLE jobno number;
BEGIN
   DBMS_JOB.SUBMIT(:jobno,
      'insert into dedi_waktu(tgl,isi)values(sysdate,''test'');' ,
      SYSDATE,
      'SYSDATE + 1/24'); --tiap jam
   COMMIT;
END;
SQL>   
/

PL/SQL procedure successfully completed.

SQL>
SQL> print jobno

     JOBNO
----------
         6

SQL>
SQL> VARIABLE jobno number;
BEGIN
   DBMS_JOB.SUBMIT(:jobno,
      'insert into dedi_waktu2(tgl,isi)values(sysdate,''test2'');' ,
      SYSDATE,
      'SYSDATE + 1/24/2/2');  --tiap 15 menit
   COMMIT;
END;
SQL>  
/

PL/SQL procedure successfully completed.

SQL>
SQL>
SQL> print jobno

     JOBNO
----------
         7

SQL> 

SQL> VARIABLE jobno number;
BEGIN
   DBMS_JOB.SUBMIT(:jobno,
      'insert into dedi_waktu2(tgl,isi)values(sysdate,''test3'');' ,
      SYSDATE,
      'SYSDATE + 1/24/2/2'); --tiap 15 menit
   COMMIT;
END;
SQL>   
/

PL/SQL procedure successfully completed.

SQL>
SQL>
SQL> print jobno

     JOBNO
----------
         8

SQL> -- continue until 11 jobs


--2-- remove job

SQL> conn <schema>
Enter password:
Connected.
SQL> exec dbms_job.remove(11);

PL/SQL procedure successfully completed.

SQL> exec dbms_job.remove(10);

PL/SQL procedure successfully completed.

SQL> exec dbms_job.remove(9);

PL/SQL procedure successfully completed.

SQL> exec dbms_job.remove(8);

PL/SQL procedure successfully completed.

SQL>  exec dbms_job.remove(7);

PL/SQL procedure successfully completed.

SQL> exec dbms_job.remove(6);

PL/SQL procedure successfully completed.

SQL> commit;

Commit complete.

SQL>
```
