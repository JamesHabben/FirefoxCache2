import struct
import datetime
import os
import csv
import argparse

argParser = argparse.ArgumentParser(description='Parse Firefox cache2 index file.')
argParser.add_argument('file', help='index file to parse')
argParser.add_argument('-o', '--output', help='CSV output file')
args = argParser.parse_args()

indexFile = open(args.file, 'r')
indexFileSize = os.path.getsize(args.file)

version = struct.unpack('>i', indexFile.read(4))[0]
lastWrittenInt = struct.unpack('>i', indexFile.read(4))[0]
dirty = struct.unpack('>i', indexFile.read(4))[0]
lastWritten = datetime.datetime.fromtimestamp( lastWrittenInt)

print version
print lastWritten
print dirty

count = 0

doCsv = False
if args.output :
    doCsv = True
    csvFile = open(args.output, 'w')
    csvWriter = csv.writer(csvFile, delimiter=',', quoting=csv.QUOTE_NONNUMERIC)
    csvWriter.writerow(('hash', 'frecency', 'expires', 'appId', 'flags', 'size'))


while indexFileSize - indexFile.tell() > 36 :
    print "loc: {0}".format(indexFile.tell()),
    hash = indexFile.read(20)
    frecency = struct.unpack('>i', indexFile.read(4))[0]
    expireTimeInt = struct.unpack('>i', indexFile.read(4))[0]
    appId = struct.unpack('>i', indexFile.read(4))[0]
    flags = struct.unpack('>B', indexFile.read(1))[0]
    fileSize = struct.unpack('>I', '\x00'+indexFile.read(3))[0]
    if hash == 0 :
        break
    expireTime = datetime.datetime.fromtimestamp(expireTimeInt)
    print "hash: {0}h".format(hash.encode('hex')),
    print "frec: {0}".format(hex(frecency)),
    print "expr: {0}".format(expireTime),
    print "apid: {0}".format(hex(appId)),
    print "flgs: {0}".format(hex(flags)),
    print "size: {0}".format(fileSize)

    if doCsv :
            csvWriter.writerow((hash.encode('hex'),
                                hex(frecency),
                                expireTime,
                                hex(appId),
                                hex(flags),
                                fileSize))

    count += 1
    isMore = fileSize - indexFile.tell()
print "\nrecord count: {0}".format(count)
if doCsv :
    print 'Data written to CSV file: {0}'.format(csvFile.name)
    csvFile.close()
