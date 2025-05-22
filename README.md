<?php
function y($x) {
    if ($x <= -0.5) {
        // Первый случай: x ≤ -1/2
        $term = pow(3, $x) - pow(abs($x), -$x);
        return -pow($x, 5) + log10(abs($term));
    } elseif ($x > -0.5 && $x < 0.5) {
        // Второй случай: -1/2 < x < 1/2
        return tan($x / (1 - $x * $x));
    } else {
        // Третий случай: x ≥ 1/2
        $arg = 1 / (4 * $x);
        if ($arg >= -1 && $arg <= 1) {
            return acos($arg);
        } else {
            return "NAN (аргумент arccos вне диапазона [-1, 1])";
        }
    }
}

// Ввод x с клавиатуры
echo "Введите значение x: ";
$x = trim(fgets(STDIN));

// Проверка, что введено число
if (!is_numeric($x)) {
    echo "Ошибка: введено не число!\n";
    exit(1);
}

// Вычисление и вывод результата
$result = y((float)$x);
echo "y($x) = " . $result . "\n";
?>
