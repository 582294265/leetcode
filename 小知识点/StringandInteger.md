* ans * 10 + digit > Integer.MAX_VALUE 会越界，那么ans > (Integer.MAX_VALUE - digit) / 10就可以了
