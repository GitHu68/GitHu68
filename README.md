- 👋 Hi, I’m @GitHu68
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
GitHu68/GitHu68 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
using System.Collections;
using UnityEngine;

public class DuckGameController : MonoBehaviour
{
    public GameObject duckPrefab; // Prefab of the duck
    public Transform[] holePositions; // Positions of the holes
    public float duckSpawnInterval = 2.0f; // Time interval between duck spawns
    public float duckLifetime = 1.0f; // Time duck is visible

    private int score = 0;

    void Start()
    {
        StartCoroutine(SpawnDucks());
    }

    IEnumerator SpawnDucks()
    {
        while (true)
        {
            // Randomly choose a hole position
            int randomHoleIndex = Random.Range(0, holePositions.Length);
            Vector3 spawnPosition = holePositions[randomHoleIndex].position;

            // Instantiate the duck prefab at the chosen position
            GameObject duck = Instantiate(duckPrefab, spawnPosition, Quaternion.identity);

            // Wait for the duck's lifetime
            yield return new WaitForSeconds(duckLifetime);

