package com.example.slideshowapp

import android.os.Bundle
import android.widget.*
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    private val images = arrayOf(
        R.drawable.hello,
        R.drawable.image,
        R.drawable.thankyouforwatching
    )

    private val captions = arrayOf(
        "Hello", "Sunset View", "Thanks for Watching"
    )

    private var currentIndex = 0

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val imageView = findViewById<ImageView>(R.id.imageView)
        val captionText = findViewById<TextView>(R.id.captionText)
        val nextButton = findViewById<Button>(R.id.nextButton)
        val prevButton = findViewById<Button>(R.id.prevButton)
        val goButton = findViewById<Button>(R.id.goButton)
        val inputIndex = findViewById<EditText>(R.id.inputIndex)

        fun updateSlide() {
            imageView.setImageResource(images[currentIndex])
            captionText.text = captions[currentIndex]
        }

        updateSlide()

        nextButton.setOnClickListener {
            currentIndex = (currentIndex + 1) % images.size
            updateSlide()
        }

        prevButton.setOnClickListener {
            currentIndex = if (currentIndex - 1 < 0) images.size - 1 else currentIndex - 1
            updateSlide()
        }

        goButton.setOnClickListener {
            val input = inputIndex.text.toString().toIntOrNull()
            if (input != null && input in images.indices) {
                currentIndex = input
                updateSlide()
            } else {
                Toast.makeText(this, "Invalid number", Toast.LENGTH_SHORT).show()
            }
        }
    }
}

![7e87eb832bb93f5cbbe99ea0a52ec95](https://github.com/user-attachments/assets/0428be0e-96ee-42b5-9e50-82c8c94e4d1e)
![f54044e745b5156c9b070cab61f1298](https://github.com/user-attachments/assets/e4e4c476-6ac5-4d52-a02a-a37bfbfd5247)
![dccf5b131e02d60f3db2ceb50557ad3](https://github.com/user-attachments/assets/3f0c65b7-7486-4fed-b582-ced42c42725a)




