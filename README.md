```
for i in range(max_iterations):
# Authority update
new_authority_scores = np.dot(adjacency_matrix.T, hub_scores)
new_authority_scores /= np.linalg.norm(new_authority_scores, ord=2) # Normalizing
# Hub update
new_hub_scores = np.dot(adjacency_matrix, new_authority_scores)
new_hub_scores /= np.linalg.norm(new_hub_scores, ord=2) # Normalizing
# Check convergence
authority_diff = np.linalg.norm(new_authority_scores - authority_scores, ord=2)
hub_diff = np.linalg.norm(new_hub_scores - hub_scores, ord=2)
if authority_diff < tol and hub_diff < tol:
break
authority_scores = new_authority_scores
hub_scores = new_hub_scores
return authority_scores, hub_scores
```
