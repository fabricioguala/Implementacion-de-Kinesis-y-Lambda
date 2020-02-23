# Implementacion-de-Kinesis-y-Lambda
/*Implementación usando Amazon Kinesis y Data Firehose*/

console.log('Loading function');

exports.handler =  (event, context, callback) => {
    /* Process the list of records and transform them */
    const output = event.records.map((record) => ({
      let entry =  (new Buffer(record.data, 'base64')).toString('utf8');
      let result = entry +"\n"
      const payload = (new Buffer(result, 'utf8')).toString('base64');
      return{
      recorId: record.recordId,
      result:'Ok',
      data: payload,
      };
    });
    console.log(`Processing completed.  Successful records ${output.length}.`);
    callback (null, { records: output });
};
