using UnityEngine;

public class ShipController : MonoBehaviour
{
    public float forwardSpeed = 25f;
    public float turnSpeed = 60f;

    void Update()
    {
        // Continuous forward movement
        transform.Translate(Vector3.forward * forwardSpeed * Time.deltaTime);

        // Capture player input (WASD or Arrow Keys)
        float turnInput = Input.GetAxis("Horizontal");
        float pitchInput = Input.GetAxis("Vertical");

        // Apply turning (yaw and pitch)
        transform.Rotate(Vector3.up, turnInput * turnSpeed * Time.deltaTime);
        transform.Rotate(Vector3.right, -pitchInput * turnSpeed * Time.deltaTime);
        
        // Optional: Add a speed boost when pressing Space
        if (Input.GetKey(KeyCode.Space))
        {
            transform.Translate(Vector3.forward * (forwardSpeed * 2) * Time.deltaTime);
        }
    }
}
