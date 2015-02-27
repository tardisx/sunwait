# sunwait

## Install

You'll need the `DateTime::Event::Sunrise` module, on debian based systems the package will be called
`libdatetime-event-sunrise-perl`.

Copy the `sunwait` script to somewhere on your path.

## Details

The script sleeps until sunset or sunrise. Useful in cron if you need something to happen in sync with
the sun. For example, doing your bitcoin mining operations while the sun provides the electricity :-)

    Usage: sunwait --lat=xxx.yyy --long=aaa.bbb [--offset=60] [--debug] up|down

You can also provide an offset to alter the time, in case you don't want it to be exactly in time with the 
sunrise/sunset. The offset is specified in minutes and can be negative or positive.

The `--debug` option will show when the script is run and the time it is going to wait for.

Example usage in cron:

    # wait for an hour after sunrise and start mining those coins!
    00 03  *  *  *  sunwait --lat=40.71 --long=-74.01 --offset=60 up && bitcoin_mine_start.sh
    # an hour before sunset, turn off the miner
    15 00  *  *  *  sunwait --lat=40.71 --long=-74.01 --offset=-60 down && bitcoin_mine_stop.sh
    
    
