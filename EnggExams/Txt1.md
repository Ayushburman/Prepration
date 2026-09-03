```bash
#!/usr/bin/env bash

# ============================================================
#                 A R C A N U M
#             THE WIZARD'S TERMINAL
# ============================================================

clear
tput civis

# ---------------- COLORS ----------------

RESET="\033[0m"
BOLD="\033[1m"
DIM="\033[2m"

PURPLE="\033[38;5;141m"
VIOLET="\033[38;5;135m"
BLUE="\033[38;5;117m"
CYAN="\033[38;5;159m"
GOLD="\033[38;5;220m"
WHITE="\033[38;5;255m"
RED="\033[38;5;203m"
GREEN="\033[38;5;114m"

# ---------------- SCREEN ----------------

trap 'tput cnorm; clear; exit' INT TERM EXIT

slow() {
    local text="$1"
    local delay="${2:-0.025}"

    while IFS= read -r -n1 char; do
        printf "%s" "$char"
        sleep "$delay"
    done <<< "$text"

    echo
}

pause() {
    sleep "${1:-0.5}"
}

line() {
    printf "${PURPLE}════════════════════════════════════════════════════════════${RESET}\n"
}

# ---------------- STAR FIELD ----------------

stars() {
    clear

    local symbols=("✦" "·" "✧" "˚" "⋆" "✶")

    for i in {1..45}; do
        x=$((RANDOM % 60))
        y=$((RANDOM % 15))

        tput cup "$y" "$x"
        printf "${VIOLET}${symbols[$((RANDOM % ${#symbols[@]}))]}${RESET}"
    done
}

# ---------------- MAGIC CIRCLE ----------------

magic_circle() {

clear

echo
echo -e "${PURPLE}                         ✦${RESET}"
echo -e "${VIOLET}                   ╭────────────╮${RESET}"
echo -e "${VIOLET}               ╭───╯   ✧  ✦     ╰───╮${RESET}"
echo -e "${PURPLE}             ╱                         ╲${RESET}"
echo -e "${PURPLE}           ╱      ╔══════════════╗      ╲${RESET}"
echo -e "${VIOLET}          │       ║              ║       │${RESET}"
echo -e "${VIOLET}          │       ║   ${GOLD}ARCANUM${VIOLET}   ║       │${RESET}"
echo -e "${VIOLET}          │       ║              ║       │${RESET}"
echo -e "${PURPLE}           ╲      ╚══════════════╝      ╱${RESET}"
echo -e "${PURPLE}             ╲                         ╱${RESET}"
echo -e "${VIOLET}               ╰───╮   ✦  ✧   ╭───╯${RESET}"
echo -e "${VIOLET}                   ╰────────────╯${RESET}"
echo -e "${PURPLE}                         ✦${RESET}"
echo

}

# ---------------- BOOT ----------------

stars

sleep 0.4

echo -e "${GOLD}${BOLD}"
cat << 'EOF'

             █████╗ ██████╗  ██████╗ █████╗ ███╗   ██╗██╗   ██╗███╗   ███╗
            ██╔══██╗██╔══██╗██╔════╝██╔══██╗████╗  ██║██║   ██║████╗ ████║
            ███████║██████╔╝██║     ███████║██╔██╗ ██║██║   ██║██╔████╔██║
            ██╔══██║██╔══██╗██║     ██╔══██║██║╚██╗██║██║   ██║██║╚██╔╝██║
            ██║  ██║██║  ██║╚██████╗██║  ██║██║ ╚████║╚██████╔╝██║ ╚═╝ ██║
            ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝╚═╝  ╚═══╝ ╚═════╝ ╚═╝     ╚═╝

EOF
echo -e "${RESET}"

echo -e "${DIM}${WHITE}              THE ARCANE TERMINAL • SCHOOL OF ANCIENT MAGIC${RESET}"
echo

pause 1

# ---------------- LOADING ----------------

echo -e "${PURPLE}Awakening the ancient runes...${RESET}"
sleep .5

for spell in \
    "Binding the moonlight" \
    "Breathing life into the glyphs" \
    "Opening the astral library" \
    "Consulting the crystal archive" \
    "Synchronizing wand core" \
    "Unlocking forbidden knowledge"
do

    printf "${VIOLET}  ◈ %-38s" "$spell"

    for i in {1..5}; do
        printf "${PURPLE}.${RESET}"
        sleep .08
    done

    echo -e " ${GREEN}DONE${RESET}"

done

sleep 1

# ---------------- PORTAL ----------------

magic_circle
pause 1

echo -e "${CYAN}${BOLD}                 THE PORTAL HAS OPENED${RESET}"
echo
echo -e "${DIM}                  Choose your path, apprentice.${RESET}"
echo

# ---------------- MENU ----------------

while true; do

    echo
    echo -e "${PURPLE}╔════════════════════════════════════════════════════════════╗${RESET}"
    echo -e "${PURPLE}║${RESET}                    ${GOLD}ARCANE CHAMBER${RESET}                     ${PURPLE}║${RESET}"
    echo -e "${PURPLE}╠════════════════════════════════════════════════════════════╣${RESET}"
    echo -e "${PURPLE}║${RESET}                                                        ${PURPLE}║${RESET}"
    echo -e "${PURPLE}║${RESET}       ${VIOLET}[1]${RESET}  ✧  Cast a spell                         ${PURPLE}║${RESET}"
    echo -e "${PURPLE}║${RESET}       ${VIOLET}[2]${RESET}  ✦  Read the ancient prophecy            ${PURPLE}║${RESET}"
    echo -e "${PURPLE}║${RESET}       ${VIOLET}[3]${RESET}  ◈  Summon a familiar                    ${PURPLE}║${RESET}"
    echo -e "${PURPLE}║${RESET}       ${VIOLET}[4]${RESET}  ☽  Enter the Forbidden Archive           ${PURPLE}║${RESET}"
    echo -e "${PURPLE}║${RESET}       ${VIOLET}[5]${RESET}  ⚗  Brew a potion                         ${PURPLE}║${RESET}"
    echo -e "${PURPLE}║${RESET}       ${VIOLET}[6]${RESET}  ☠  Leave the chamber                     ${PURPLE}║${RESET}"
    echo -e "${PURPLE}║${RESET}                                                        ${PURPLE}║${RESET}"
    echo -e "${PURPLE}╚════════════════════════════════════════════════════════════╝${RESET}"

    echo
    read -rp "$(echo -e "${GOLD}☽  Enter your choice > ${RESET}")" choice

    case "$choice" in

        1)
            clear

            echo -e "${VIOLET}"
            cat << 'EOF'

                    ✦
                   / \
                  /   \
                 /  ✧  \
                /       \
          ✧─────╯         ╰─────✧

                  SPELLBOOK

          1. LUMEN AETERNUM
          2. IGNIS
          3. AERO
          4. UMBRA
          5. STELLARIS

EOF
            echo -e "${RESET}"

            read -rp "$(echo -e "${CYAN}Cast > ${RESET}")" spell

            clear

            echo
            echo -e "${PURPLE}                 ✧ ✦ ✧${RESET}"
            echo
            echo -e "${GOLD}              ${spell^^}${RESET}"
            echo
            echo -e "${VIOLET}                  ✦${RESET}"
            echo -e "${VIOLET}                ✦   ✦${RESET}"
            echo -e "${PURPLE}              ✧       ✧${RESET}"
            echo -e "${BLUE}           ✦      ◉      ✦${RESET}"
            echo -e "${PURPLE}              ✧       ✧${RESET}"
            echo -e "${VIOLET}                ✦   ✦${RESET}"
            echo -e "${VIOLET}                  ✦${RESET}"
            echo

            for i in {1..8}; do
                printf "${PURPLE}              ✦${RESET}"
                sleep .08
            done

            echo
            echo
            echo -e "${GREEN}${BOLD}             SPELL SUCCESSFUL${RESET}"

            pause 2
            clear
            ;;

        2)
            clear

            echo -e "${GOLD}"
            cat << 'EOF'

                    THE ANCIENT PROPHECY

        "When the stars fall silent
         and the moon forgets its name,

         the one who walks between
         shadow and light

         shall open the final door.

         Beyond it waits not death,

         but knowledge."

EOF
            echo -e "${RESET}"

            echo
            read -rp "Press ENTER to return..."
            clear
            ;;

        3)
            clear

            echo -e "${VIOLET}"
            cat << 'EOF'

                       /\_/\
                      ( o.o )
                       > ^ <
                     /       \
                    /  ✦ ✦    \
                   /___________\

                 ✧ FAMILIAR SUMMONED ✧

EOF
            echo -e "${RESET}"

            echo -e "${CYAN}Your familiar watches silently.${RESET}"
            echo
            read -rp "Press ENTER..."
            clear
            ;;

        4)
            clear

            echo -e "${RED}${BOLD}"
            cat << 'EOF'

                 ☠  FORBIDDEN ARCHIVE  ☠

             ╔══════════════════════════╗
             ║                            ║
             ║       ACCESS DENIED       ║
             ║                            ║
             ║   These books remember    ║
             ║   those who read them.    ║
             ║                            ║
             ╚══════════════════════════╝

EOF
            echo -e "${RESET}"

            sleep 1
            echo -e "${DIM}The archive whispers your name...${RESET}"

            sleep 2
            clear
            ;;

        5)
            clear

            echo -e "${GREEN}"
            cat << 'EOF'

                    ⚗  ARCANE POTION LAB  ⚗

              ┌──────────────────────────┐
              │                          │
              │          ______          │
              │         /      \         │
              │        /  ✦✦✦   \        │
              │       |   ~~~~   |       │
              │       |  ~~~~~~  |       │
              │        \________/        │
              │                          │
              └──────────────────────────┘

EOF
            echo -e "${RESET}"

            echo "Mixing moonwater..."
            sleep .7
            echo "Adding phoenix ash..."
            sleep .7
            echo "Stirring clockwise..."
            sleep .7
            echo "Adding one final rune..."
            sleep .7

            echo
            echo -e "${GOLD}${BOLD}             POTION COMPLETE ✦${RESET}"

            sleep 2
            clear
            ;;

        6)
            clear
            echo
            echo -e "${PURPLE}             The candles extinguish...${RESET}"
            sleep .7
            echo -e "${VIOLET}             The portal closes...${RESET}"
            sleep .7
            echo -e "${BLUE}             The magic sleeps.${RESET}"
            sleep 1

            echo
            echo -e "${GOLD}             Until the next moon.${RESET}"
            echo

            tput cnorm
            exit
            ;;

        *)
            echo -e "${RED}The runes do not recognize that command.${RESET}"
            sleep 1
            clear
            ;;

    esac

done

```
