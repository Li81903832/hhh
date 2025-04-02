# code2flow-in-java   

```
@Test 
void whenSingleMatchByToken_returnsNode() { 
Node targetNode = createNode("targetFunc", "TestGroup", "TestFile"); 
SubsetParams params = new SubsetParams("targetFunc", 0, 0); 
List<Node> nodes = Collections.singletonList(targetNode); 
Node result = engine.findTargetNode(params, nodes); 
assertEquals(targetNode, result); 
} 
// 测试通过 token_with_ownership 匹配 
@Test 
void whenSingleMatchByTokenWithOwnership_returnsNode() { 
Node targetNode = createNodeWithOwnership("method", "TestClass", "TestFile"); 
SubsetParams params = new SubsetParams("TestClass.method", 0, 0); 
Node result=engine.findTargetNode(params,Collections.singletonList
(targetNode)); 
assertEquals(targetNode, result); 
} 
// 测试无匹配节点时抛出异常 
@Testvoid whenNoMatchingNode_throwsException() { 
SubsetParams params = new SubsetParams("nonexistent", 0, 0); 
List<Node> nodes = Arrays.asList( createNode("func1", "Group1", "File1"), 
createNode("func2", "Group2", "File2") ); 
Exception e = assertThrows(IllegalArgumentException.class, () -> 
engine.findTargetNode(params, nodes)); 
assertTrue(e.getMessage().contains("Could not find node 'nonexistent'")); 
} 
// 测试通过 name 匹配 
@Test 
void whenSingleMatchByName_returnsNode() { 
Node targetNode = createNodeWithOwnership("method", "TestClass", "TestFile"); 
String expectedName = "TestFile::TestClass.method"; 
SubsetParams params = new SubsetParams(expectedName, 0, 0); 
Node result = engine.findTargetNode(params, Collections.singletonList(targetNode)); 
assertEquals(targetNode, result); 
}
```
