###整数和小数小于两位小数的直接返回原数据，大于两位的保留两位小数且不四舍五入
####php
    function formatNumber($number, $decimals = 0, $rounded = true) {
        $new_number = round($number, $decimals);
        if ($rounded) {
            return $new_number;
        }
        if ($new_number > $number) {
            $new_number -= 1 / pow(10, $decimals);
        }
        return $new_number;
    }
