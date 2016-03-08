###获取随机密码
####php

    /**
     * @param $bit_num 多少位的密码
     * @param string $type 类型：num, char, mix
     * @param bool $case_sensitive 是否区分大小写
     * @return string
     */
    function getRandomPass($bit_num, $type = 'mix', $case_sensitive = true) {
        $number = '0123456789';
        $low_case = 'abcdefghijklmnopqrstuvwxyz';
        $up_case = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';

        switch ($type) {
            case 'num':
                $chars = $number;
                break;
            case 'char':
                if ($case_sensitive) {
                    $chars = $low_case . $up_case;
                } else {
                    $chars = $low_case;
                }
                break;
            default :
                if ($case_sensitive) {
                    $chars = $low_case . $up_case;
                } else {
                    $chars = $low_case;
                }
                $chars .= $number;
                break;
        }

        $times = 0;
        $pass = '';
        $chars_length = strlen($chars);
        while ($times < $bit_num) {
            $pass .= substr($chars, mt_rand() % $chars_length, 1);
        }

        return $pass;
    }
