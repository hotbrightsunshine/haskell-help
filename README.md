# haskell-help

🗝️ A repository with some solution to common Haskell configuration problems.

# Create a new stack project
## Preface
Since GHC 9.0.2 is not compatible with HLS 1.7.0.0 and Stack 2.7.3, you will need to force Stack to use a compatible version og GHC such as 8.10.7 (which is the one recommended by GHCup).

## How to solve?
In order to use a fully functional Stack configuration, you'll need to:

- **Create a `hie.yaml` file as follows:**
    ```
    cradle:
        stack:
    ```
    To not have issues with cradles and your HLS

- **Add the following line to your `config.yaml` file (usually located in ~/.stack/config.yaml):**
    ```
    allow-newer: true
    ```
    To make the following step work. This is suggested by Stack.

- **Change the `resolver` entry in the `stack.yaml` file as follows:**
    ```
    resolver: 
        lts-18.28 (this is just an example)
    ```
    That is because you need to specify which GHC version to use. Stack will download that from Stackage, so you'll need to check which is the version of your GH Compiler that corrisponds to the one in the Stackage database.

- **If you have issues with your *standard* ``Setup.hs`` file, add the following line to the dependencies in your `package.yaml`:**
    ```
    - Cabal >= 3.2.1.0
    ```

