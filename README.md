# cpd.pl
#count frequencies of different numbers and show an accumulative frequency.   

!usr/bin/perl -w

#first to identify if there is a list or a file
   if (-e $ARGV[0]){
       @a=();
       open (IN, "<$ARGV[0]");
       while (<IN>){
       chomp($_);
       push (@a, $_);
       }
      close IN;
    else {
     @a = @ARGV;
      }

#make the data after re-arrangement (from small value to large) to be a new list
 @sa = sort {$a <=> $b} @a;
 print "@sa\n";

 #count individual numbers
 $n = $sa[0];
 $f = 1;
 $sum = 0;
 for ($i = 1; $i<=$#sa; $i=$i+1){
 
          if ($sa[$i] eq $n) {
              $f = $f + 1;
          }
          else {
          $sum += $f;
          print "$n\t$sum\n";
          $n = $sa[$i];
          $f = 1;
          }
      }
     print "$n\t$sum\n";

