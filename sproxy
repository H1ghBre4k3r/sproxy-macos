#!/bin/bash

me=`basename "$0"`

function printHelp() {
    echo "Usage: $me <option> [params]"
    echo ""
    echo "Where <option> is one of the following:"
    echo -e "\t" "-h,--help" 
    echo -e "\t\t\t"    "Display this dialog"
    echo -e "\t" "-v,--version"
    echo -e "\t\t\t"    "Display the version"
    echo -e "\t" "-l,--list"
    echo -e "\t\t\t"    "List all available interfaces"
    echo -e "\t" "-e,--enable <interface>"
    echo -e "\t\t\t"    "Turn on the SOCKS proxy for the provided inteface"
    echo -e "\t" "-d,--disable <interface>"
    echo -e "\t\t\t"    "Turn off the SOCKS proxy for the provided inteface"
}

function printVersion() {
    echo "v0.1.0"
}

function listInterfaces() {
    networksetup -listallnetworkservices
}

function enableInterface() {
    networksetup -setsocksfirewallproxystate "$1" on
}

function disableInterface() {
    networksetup -setsocksfirewallproxystate "$1" off
}

function changeSettings() {
    networksetup -setsocksfirewallproxy $1 $2 $3 $4 $5 $6
}

if [ $# -eq 0 ]; then
    echo "No valid argument provided!"
    printHelp
    exit -1
fi

while test $# -gt 0; do
    case "$1" in
        -h|--help)
            printHelp
            exit
        ;;
        -v|--version)
            printVersion
            exit
        ;;
        -l|--list)
            listInterfaces
            exit
        ;;
        -e|--enable)
            enableInterface "$2"
            exit
        ;;
        -d|--disable)
            disableInterface "$2"
            exit
        ;;
        *)
            echo "Invalid command '$1'"
            printHelp
            exit -1
            ;;
    esac
done