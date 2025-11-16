# bentoumia1#!/usr/bin/env bash
# Guessing Game - Guess the number of files in the current directory

function get_file_count {
    local count=$(ls -1 | wc -l)
    echo $count
}

function get_user_guess {
    echo "How many files are in the current directory?"
    read guess
    echo $guess
}

function main {
    local file_count=$(get_file_count)
    local user_guess=-1
    
    echo "Welcome to the Guessing Game!"
    echo ""
    
    while [[ $user_guess -ne $file_count ]]
    do
        user_guess=$(get_user_guess)
        
        if [[ $user_guess -lt $file_count ]]
        then
            echo "Your guess is too low. Try again!"
            echo ""
        elif [[ $user_guess -gt $file_count ]]
        then
            echo "Your guess is too high. Try again!"
            echo ""
        else
            echo "Congratulations! You guessed the correct number of files!"
            echo ""
        fi
    done
}

main
