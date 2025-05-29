import React from "react";
import { Button } from "@/components/ui/button";
import { Tabs, TabsList, TabsTrigger } from "@/components/ui/tabs";

const categories = [
  "Men",
  "Women",
  "Mobile Covers",
  "Accessories",
  "Sneakers",
  "Official Merch",
  "Heavy Duty",
  "Plus Size",
  "Live Now"
];

const products = [
  {
    name: "Denim Jeans (Men)",
    price: "₹1,499",
    offer: "30% OFF",
    image: "/images/denim-men.jpg",
    category: "Men",
  },
  {
    name: "Oversized T-Shirt (Women)",
    price: "₹999",
    offer: "40% OFF",
    image: "/images/tshirt-women.jpg",
    category: "Women",
  },
  {
    name: "Colorful Joggers",
    price: "₹1,699",
    offer: "Buy 2 at ₹1699",
    image: "/images/joggers.jpg",
    category: "Men",
  },
  {
    name: "SpongeBob Mobile Cover",
    price: "₹399",
    offer: "New Arrival",
    image: "/images/mobile-cover.jpg",
    category: "Mobile Covers",
  },
];

export default function Home() {
  return (
    <main className="bg-gradient-to-r from-white to-[#f5f5dc] text-[#1a1a1a] min-h-screen font-sans">
      {/* Header */}
      <header className="bg-white shadow-sm sticky top-0 z-50 py-4 px-6 flex items-center justify-between">
        <h2 className="text-3xl font-extrabold text-[#1a1a1a]">Zosfar</h2>
        <nav className="space-x-6 text-sm font-medium hidden md:block">
          {categories.map(cat => (
            <a key={cat} href="#" className="hover:text-[#c4a484] transition-colors">{cat}</a>
          ))}
        </nav>
        <div className="space-x-4">
          <Button variant="ghost">Login</Button>
          <Button className="bg-[#c4a484] text-white hover:bg-[#b9936c]">Cart</Button>
        </div>
      </header>

      {/* Hero Banner */}
      <section className="w-full h-[80vh] bg-cover bg-center" style={{ backgroundImage: "url('/images/zosfar-banner.jpg')" }}>
        <div className="w-full h-full bg-white bg-opacity-80 flex flex-col justify-center items-center text-center px-4">
          <h1 className="text-5xl font-bold mb-4 text-[#c4a484]">Zosfar</h1>
          <p className="text-lg text-gray-700 mb-6">Gen-Z Style | Bold Fashion | Youthwear Revolution</p>
          <Button className="text-white bg-[#c4a484] hover:bg-[#b9936c] text-lg px-6 py-3 rounded-xl">Shop Now</Button>
        </div>
      </section>

      {/* Categories */}
      <section className="py-10 px-6 md:px-16">
        <Tabs defaultValue="Men" className="w-full">
          <TabsList className="flex justify-center gap-4 flex-wrap">
            {categories.map((cat) => (
              <TabsTrigger key={cat} value={cat} className="text-[#1a1a1a] font-medium px-4 py-2 rounded-full hover:bg-[#e6e6e6]">{cat}</TabsTrigger>
            ))}
          </TabsList>

          {categories.map((cat) => (
            <div key={cat} value={cat} className="mt-10 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10">
              {products.filter(p => p.category === cat).map((product, index) => (
                <div key={index} className="bg-white border border-[#eaeaea] p-5 rounded-3xl shadow-md hover:shadow-xl transition-shadow">
                  <img src={product.image} alt={product.name} className="w-full h-64 object-cover rounded-2xl mb-4" />
                  <h3 className="text-xl font-semibold mb-2 text-[#1a1a1a]">{product.name}</h3>
                  <p className="text-[#555] mb-1">{product.price}</p>
                  <p className="text-[#28a745] font-semibold">{product.offer}</p>
                </div>
              ))}
            </div>
          ))}
        </Tabs>
      </section>

      {/* Footer */}
      <footer className="bg-[#f1f1f1] py-12 text-center text-[#777] mt-16">
        <div className="grid md:grid-cols-4 gap-10 px-6">
          <div>
            <h4 className="text-[#1a1a1a] font-semibold mb-4">Company</h4>
            <ul className="space-y-2">
              <li><a href="#">About Us</a></li>
              <li><a href="#">Careers</a></li>
              <li><a href="#">Sitemap</a></li>
            </ul>
          </div>
          <div>
            <h4 className="text-[#1a1a1a] font-semibold mb-4">Help</h4>
            <ul className="space-y-2">
              <li><a href="#">Contact Us</a></li>
              <li><a href="#">Track Order</a></li>
              <li><a href="#">Return Policy</a></li>
              <li><a href="#">Privacy Policy</a></li>
            </ul>
          </div>
          <div>
            <h4 className="text-[#1a1a1a] font-semibold mb-4">Categories</h4>
            <ul className="space-y-2">
              {categories.map((cat, i) => <li key={i}><a href="#">{cat}</a></li>)}
            </ul>
          </div>
          <div>
            <h4 className="text-[#1a1a1a] font-semibold mb-4">Connect</h4>
            <p className="mb-2">Email: support@zosfar.com</p>
            <p>Phone: +91-9876543210</p>
          </div>
        </div>
        <p className="mt-10">&copy; 2025 Zosfar. All Rights Reserved.</p>
      </footer>
    </main>
  );
}
