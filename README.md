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
