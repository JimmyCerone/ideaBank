Deliver Infrastructure as Code. 

Super powerful because you can have your build process on hand in case it goes down or you want to edit it. Kind of like an easy way to manage infrastructure in a way that helps. [[Humans have limited memories]].

## General
- Declarative language that focuses on the goal rather than the steps to get there
- Does not pay attention to order except where there are dependent relationships (infra in one place is used by other infra in another place)

## Import
- Pulls an existing resource into terraform state, which can be local or remote

## Data
- Pulls in data sources for use within the infra

## Locals
- Local variables for use within a single file

## Provider
- Describes which provider the infrastructure comes from. #PlugIn 

## Module
- Basically an import from another file. 