# AI-TECH-AGRI
// app/layout.tsx
import './globals.css';
import { Inter } from 'next/font/google';
import { Metadata } from 'next';

const inter = Inter({ subsets: ['latin'] });

export const metadata: Metadata = {
  title: 'AgriAI - Smart Farming Platform',
  description: 'AI-powered agriculture insights for a sustainable future',
};

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body className={inter.className + ' bg-gray-50 text-gray-900'}>
        {children}
      </body>
    </html>
  );
}


// app/page.tsx (Home)
import Link from 'next/link';

export default function HomePage() {
  return (
    <main className="min-h-screen flex flex-col items-center justify-center text-center p-4">
      <h1 className="text-4xl font-bold mb-4">Welcome to AgriAI 🌾</h1>
      <p className="mb-6 max-w-xl">
        Use AI to gain insights on soil, climate, and farming. Upload data, visualize trends, and get sustainable recommendations.
      </p>
      <div className="flex gap-4">
        <Link href="/upload" className="px-6 py-3 bg-green-600 text-white rounded-2xl shadow hover:bg-green-700">
          Upload Data
        </Link>
        <Link href="/dashboard" className="px-6 py-3 border border-green-600 text-green-700 rounded-2xl hover:bg-green-100">
          View Dashboard
        </Link>
      </div>
    </main>
  );
}


// app/upload/page.tsx
'use client';
import { useState } from 'react';

export default function UploadPage() {
  const [file, setFile] = useState<File | null>(null);

  const handleUpload = () => {
    if (!file) return alert('Please select a file first');
    alert(`Uploading: ${file.name}`);
    // Implement actual upload logic here
  };

  return (
    <main className="p-6">
      <h2 className="text-2xl font-bold mb-4">Upload Soil / Farm Data</h2>
      <input
        type="file"
        onChange={(e) => setFile(e.target.files?.[0] || null)}
        className="mb-4"
      />
      <button
        onClick={handleUpload}
        className="px-6 py-2 bg-blue-600 text-white rounded-xl hover:bg-blue-700"
      >
        Upload
      </button>
    </main>
  );
}


// app/dashboard/page.tsx
export default function DashboardPage() {
  return (
    <main className="p-6">
      <h2 className="text-2xl font-bold mb-6">📊 Dashboard Insights</h2>
      <div className="grid gap-4 md:grid-cols-2">
        <div className="bg-white shadow rounded-2xl p-4">
          <h3 className="text-lg font-semibold mb-2">Soil Analysis</h3>
          <p>Coming soon: AI-generated soil quality & nutrient charts.</p>
        </div>
        <div className="bg-white shadow rounded-2xl p-4">
          <h3 className="text-lg font-semibold mb-2">Weather Forecast</h3>
          <p>Coming soon: API-integrated weather trends & alerts.</p>
        </div>
        <div className="bg-white shadow rounded-2xl p-4">
          <h3 className="text-lg font-semibold mb-2">Earthquake Monitor</h3>
          <p>Coming soon: Real-time seismic activity by region.</p>
        </div>
        <div className="bg-white shadow rounded-2xl p-4">
          <h3 className="text-lg font-semibold mb-2">Recommendations</h3>
          <p>Coming soon: AI-driven farming advice tailored to your data.</p>
        </div>
      </div>
    </main>
  );
}


// tailwind.config.ts
import type { Config } from 'tailwindcss';

const config: Config = {
  content: ['./app/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {},
  },
  plugins: [],
};
export default config;


// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};


// styles/globals.css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  font-family: 'Inter', sans-serif;
  background-color: #f9fafb;
}
