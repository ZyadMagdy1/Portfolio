import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Instagram } from "lucide-react";
import { motion } from "framer-motion";
import { useRef, useState } from "react";

export default function Portfolio() {
  const [selectedImage, setSelectedImage] = useState(null);
  const scrollRef = useRef(null);

  const scroll = (direction) => {
    if (scrollRef.current) {
      scrollRef.current.scrollBy({
        left: direction === "left" ? -400 : 400,
        behavior: "smooth",
      });
    }
  };

  const projects = [
    {
      id: 1,
      title: "Creative Poster Design",
      image: "https://i.postimg.cc/4yLCWtwd/image-1.png",
      description: "A bold and artistic poster layout with a modern twist."
    },
    {
      id: 2,
      title: "Vintage Drink Ad",
      image: "https://i.postimg.cc/PxSFHHDV/SPIRO-SPATHIS.jpg",
      description: "Retro-style ad for a classic beverage brand."
    },
    {
      id: 3,
      title: "Abstract Motion Design",
      image: "https://i.postimg.cc/BQ2NTWkH/Untitled-1-gifp.jpg",
      description: "Dynamic animated graphic showcasing abstract visual elements."
    },
    {
      id: 4,
      title: "Juhayna Juice Promo",
      image: "https://i.postimg.cc/J4kK6Zp2/juhayna.jpg",
      description: "Colorful ad design for Juhayna fruit juices."
    },
    {
      id: 5,
      title: "Minimalist Poster Concept",
      image: "https://i.postimg.cc/Y2sMfKPx/image-1.png",
      description: "Sleek, clean poster with minimalist design principles."
    },
    {
      id: 6,
      title: "Tea Product Visual",
      image: "https://i.postimg.cc/4Np4J28b/Tea2.jpg",
      description: "Soft-toned ad for a tea product, designed for elegance and clarity."
    },
    {
      id: 7,
      title: "Creative Food Poster",
      image: "https://i.postimg.cc/y6cC9gF7/Untitled-2.jpg",
      description: "Appetizing food design blending bold text and rich visuals."
    },
  ];

  return (
    <div className="min-h-screen bg-gray-100 p-6 font-sans">
      <motion.div 
        className="flex justify-center mb-4"
        initial={{ opacity: 0, scale: 0.5 }} 
        animate={{ opacity: 1, scale: 1 }} 
        transition={{ duration: 0.8 }}
      >
        <img
          src="https://i.postimg.cc/dt8PLx9S/LETTER-Z-LOGO-DESIGN-For-Sale-Hire-Us-To-Get-The-Best-Graphic-Design-Services.png"
          alt="Zyad Logo"
          className="w-32 h-32 object-contain drop-shadow-lg"
        />
      </motion.div>

      <nav className="flex justify-center gap-6 mb-8">
        <a href="#portfolio" className="text-blue-600 font-medium hover:underline">Portfolio</a>
        <a href="#about" className="text-blue-600 font-medium hover:underline">About Me</a>
        <a href="#contact" className="text-blue-600 font-medium hover:underline">Contact Me</a>
      </nav>

      <header className="text-center mb-12">
        <h1 className="text-4xl font-bold mb-2">Zyad Magdy</h1>
        <p className="text-lg text-gray-600">Graphic Designer | Social Media Specialist</p>
        <a href="https://www.instagram.com/zyvvd_m" target="_blank">
          <Button className="mt-4 flex items-center gap-2">
            <Instagram size={18} /> Follow me
          </Button>
        </a>
      </header>

      <section id="about" className="max-w-4xl mx-auto mb-16">
        <h2 className="text-2xl font-semibold mb-4">About Me</h2>
        <p className="text-gray-700 leading-relaxed">
          I am a graphic designer with a keen eye for detail and a passion for creating visually compelling designs. I specialize in social media design, helping businesses build their brand presence and engage their audience through eye-catching visuals.
        </p>
      </section>

      <section id="portfolio" className="max-w-6xl mx-auto">
        <h2 className="text-2xl font-semibold mb-6 text-center">My Work</h2>
        <div className="relative">
          <button onClick={() => scroll("left")} className="absolute left-0 top-1/2 -translate-y-1/2 z-10 bg-white shadow-md rounded-full p-2">
            ◀
          </button>
          <div ref={scrollRef} className="flex gap-6 overflow-x-auto scroll-smooth pb-4 px-6">
            {projects.map((project) => (
              <motion.div
                key={project.id}
                whileHover={{ scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
                className="min-w-[300px] cursor-pointer"
                onClick={() => setSelectedImage(project.image)}
              >
                <Card className="overflow-hidden rounded-2xl shadow-md w-72">
                  <img src={project.image} alt={project.title} className="w-full h-64 object-cover transition-transform duration-300" />
                  <CardContent className="p-4">
                    <h3 className="text-lg font-medium">{project.title}</h3>
                    <p className="text-sm text-gray-600 mt-2">{project.description}</p>
                  </CardContent>
                </Card>
              </motion.div>
            ))}
          </div>
          <button onClick={() => scroll("right")} className="absolute right-0 top-1/2 -translate-y-1/2 z-10 bg-white shadow-md rounded-full p-2">
            ▶
          </button>
        </div>
      </section>

      <section id="contact" className="max-w-3xl mx-auto mt-16 text-center">
        <h2 className="text-2xl font-semibold mb-4">Contact Me</h2>
        <p className="text-gray-700">You can reach out to me via Instagram or email: <a href="mailto:zyad@example.com" className="text-blue-600 hover:underline">zyad@example.com</a></p>
      </section>

      {selectedImage && (
        <div className="fixed inset-0 bg-black bg-opacity-80 flex items-center justify-center z-50" onClick={() => setSelectedImage(null)}>
          <img src={selectedImage} alt="Full" className="max-w-4xl max-h-[90vh] object-contain rounded-lg shadow-lg" />
        </div>
      )}
    </div>
  );
}
  
