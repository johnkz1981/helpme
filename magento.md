if (!(bool)$debugMode && extension_loaded('xdebug')) {
    if (function_exists('xdebug_disable')) {
        xdebug_disable();
    }
}
