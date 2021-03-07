# mysql_sys.x-ps_schema_table_statistics_io-

SELECT 
    EXTRACT_SCHEMA_FROM_FILE_NAME(`performance_schema`.`file_summary_by_instance`.`FILE_NAME`) AS `table_schema`,
    EXTRACT_TABLE_FROM_FILE_NAME(`performance_schema`.`file_summary_by_instance`.`FILE_NAME`) AS `table_name`,
    SUM(`performance_schema`.`file_summary_by_instance`.`COUNT_READ`) AS `count_read`,
    SUM(`performance_schema`.`file_summary_by_instance`.`SUM_NUMBER_OF_BYTES_READ`) AS `sum_number_of_bytes_read`,
    SUM(`performance_schema`.`file_summary_by_instance`.`SUM_TIMER_READ`) AS `sum_timer_read`,
    SUM(`performance_schema`.`file_summary_by_instance`.`COUNT_WRITE`) AS `count_write`,
    SUM(`performance_schema`.`file_summary_by_instance`.`SUM_NUMBER_OF_BYTES_WRITE`) AS `sum_number_of_bytes_write`,
    SUM(`performance_schema`.`file_summary_by_instance`.`SUM_TIMER_WRITE`) AS `sum_timer_write`,
    SUM(`performance_schema`.`file_summary_by_instance`.`COUNT_MISC`) AS `count_misc`,
    SUM(`performance_schema`.`file_summary_by_instance`.`SUM_TIMER_MISC`) AS `sum_timer_misc`
FROM
    `performance_schema`.`file_summary_by_instance`
GROUP BY `table_schema` , `table_name`
