# AST - Abstract Syntax Tree

## Examples

### Function Call

Source Code
```
add(4, 2)
```

AST
```
ASTNode::FunctionCall {
    name:   "add",
    params: [ASTNode::Number(4), ASTNode::Number(2)],
}
```

### If Expression

Source Code
```
if add(4, 2) == 1 then 100 else 200
```

AST
```
ASTNode::IfExpression {
  condition: ASTNode::OperatorCall {
    op:    "==",
    left:  ASTNode::FunctionCall { .. },
    right: ASTNode::Number(1)
  }
  then: ASTNode::Number(100),
  else: ASTNode::Number(200),
}
```

## Usage

An AST is generally constructed by streaming tokens from an [lexer](content/lexer.md) or [tokenizer](content/tokenizer.md) into a parser where the parser is statefully aware what it expects and what to do with what tokens in which scenarios\
\
Recursive descent is a common approach
