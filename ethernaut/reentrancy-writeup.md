# Ethernaut — Reentrancy Challenge Writeup

## Objective
Drain all funds from the vulnerable contract.

## Vulnerability
Contract sends ETH before updating balance state.

## Exploit Steps
1. Deploy attacker contract
2. Call deposit() with small amount
3. Call withdraw() — triggers fallback loop
4. Fallback re-enters withdraw() before balance resets
5. Repeat until contract drained

## Fix
Follow Checks-Effects-Interactions pattern.
Update state BEFORE external call.

## Lesson Learned
Never trust external calls. Always update state first.
