# Day 38 – YAML Basics

## 1.	Task 1: Key-Value Pairs
   * Create person.yaml that describes yourself with:
     name, role ,experience_years, learning (a boolean true/false)
     <img width="640" height="321" alt="image" src="https://github.com/user-attachments/assets/e900b8ad-947b-460d-a39e-d2939f4b26a6" /> 

   * Verify: Run cat person.yaml — does it look clean? No tabs? 
    <img width="640" height="321" alt="image" src="https://github.com/user-attachments/assets/c8ed85d5-53d6-47a5-91a5-3575404c7b1c" />

## 2. Task 2: Lists 
   *  Add to person.yaml:
   *	tools — a list of 5 DevOps tools you know or are learning
   *	hobbies — a list using the inline format [item1, item2]
  
  1. Block list format:
      * block sequence or multi-line array.
      * written using hyphens (-) with indentation, where each item appears on a separate line. 
       <img width="678" height="276" alt="image" src="https://github.com/user-attachments/assets/d4a2403b-4c59-4fff-b631-911a6f762851" />

  2. Inline list format:
      * written inside square brackets [ ].
      * items separated by commas on the same line.
        <img width="669" height="128" alt="image" src="https://github.com/user-attachments/assets/82bb7573-544e-489c-9cec-c9057d044114" />

## 3.	Task 3: Nested Objects
   *	Create server.yaml that describes a server:
   *	server with nested keys: name, ip, port
   *	database with nested keys: host, name, credentials (nested further: user, password)
     <img width="871" height="448" alt="image" src="https://github.com/user-attachments/assets/bd8a8916-d329-4ff0-82a0-4f8dad7a3f4f" />
   * verify the yaml file:
     <img width="933" height="464" alt="image" src="https://github.com/user-attachments/assets/80ee6d14-0b2e-4b38-b820-fd2dd2d743a0" />
   ### Notes:
         1.	YAML does not allow tabs for indentation.
         2.	Tabs are invalid in YAML.
         3.	If you replace spaces with a tab, the validator will throw an error

## 4.	Task 4: Multi-line Strings
      •	In server.yaml, add a startup_script field using:
      •	The | block style (preserves newlines)
      •	The > fold style (folds into one line)
    
  <img width="941" height="315" alt="image" src="https://github.com/user-attachments/assets/ac9eabbd-3c6a-4600-96be-8c49fcc4a1bf" />

### Notes: 
    a.	| (Literal Block Style):
        1.	Preserves line breaks exactly as written.
        2.	Each line remains on a new line when parsed.
        3.	Used when formatting matters.

    b.	> (Folded Style):
        1.	Folds multiple lines into a single line separated by spaces.
        2.	Used when you want to write long text in multiple lines for readability, but treat it as one line.

## 5.	Task 5: Validate Your YAML
       •	Install yamllint YAML validator:  
           * sudo apt update
           * sudo apt install yamllint
           * Check installation: yamllint –version  
        
  <img width="821" height="90" alt="image" src="https://github.com/user-attachments/assets/53063ec5-90ea-4f88-8c10-37b5259fa8ba" />

      •	Validate both your YAML files
         
         1. yamllint person.yaml 
  <img width="970" height="474" alt="image" src="https://github.com/user-attachments/assets/f85b5382-f742-4fd5-90fa-fd64fa1d2d23" />
         
         2. yamllint server.yaml 
  <img width="893" height="270" alt="image" src="https://github.com/user-attachments/assets/c6e5ddb2-e78e-49e3-a0af-bf795d833194" />

      •	Fix it and validate again: 
         
         1. fix all indentation error person.yaml :
  <img width="966" height="65" alt="image" src="https://github.com/user-attachments/assets/5ea1ab75-29f0-4ff2-996e-441224d8e2ac" />
        
        2. fix all indentation error server.yaml : 
  <img width="886" height="71" alt="image" src="https://github.com/user-attachments/assets/2cddb74a-49d9-44ab-aa78-6055c90707b7" />

## 6.	Task 6: Spot the Difference 
      # Block 1 - correct
      name: devops
      tools:
        - docker
        – Kubernetes


      # Block 2 - broken
      name: devops
      tools:
      - docker
        - kubernetes

      # Block 1: 
        1. tools: is the parent key
        2. The list items are indented with 2 spaces
        3. Both list items align correctly under tools
  
      # Block 2: 
        1. docker is not indented under tools:
        2. YAML expects list items to be nested with spaces under the key



        







