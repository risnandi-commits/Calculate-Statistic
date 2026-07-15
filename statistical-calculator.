```react
import React, { useState, useEffect } from 'react';

export default function App() {
  const [currentInput, setCurrentInput] = useState('');
  const [dataset, setDataset] = useState([]);
  const [result, setResult] = useState('');
  const [history, setHistory] = useState('');

  // Efek suara sederhana (opsional, menggunakan Web Audio API jika diizinkan browser)
  const playClickSound = () => {
    try {
      const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      const oscillator = audioCtx.createOscillator();
      const gainNode = audioCtx.createGain();
      oscillator.type = 'sine';
      oscillator.frequency.setValueAtTime(800, audioCtx.currentTime);
      gainNode.gain.setValueAtTime(0.1, audioCtx.currentTime);
      oscillator.connect(gainNode);
      gainNode.connect(audioCtx.destination);
      oscillator.start();
      oscillator.stop(audioCtx.currentTime + 0.05);
    } catch (e) {
      // Ignore if audio is not supported or blocked
    }
  };

  const handleTouch = () => {
    playClickSound();
  };

  const inputNumber = (num) => {
    handleTouch();
    setCurrentInput((prev) => prev + num);
    setResult('');
  };

  const addData = () => {
    handleTouch();
    if (currentInput.trim() !== '' && !isNaN(currentInput)) {
      setDataset([...dataset, parseFloat(currentInput)]);
      setCurrentInput('');
      setResult('');
    }
  };

  const clearAll = () => {
    handleTouch();
    setDataset([]);
    setCurrentInput('');
    setResult('');
    setHistory('');
  };

  const deleteLast = () => {
    handleTouch();
    setCurrentInput((prev) => prev.slice(0, -1));
  };

  // --- Fungsi-fungsi Statistik ---
  const calcMean = () => {
    handleTouch();
    if (dataset.length === 0) return setResult('Data Kosong');
    const mean = dataset.reduce((a, b) => a + b, 0) / dataset.length;
    setHistory('Mean (Rata-rata)');
    setResult(mean.toFixed(4).replace(/\.?0+$/, ''));
  };

  const calcMedian = () => {
    handleTouch();
    if (dataset.length === 0) return setResult('Data Kosong');
    const sorted = [...dataset].sort((a, b) => a - b);
    const mid = Math.floor(sorted.length / 2);
    const median = sorted.length % 2 !== 0 ? sorted[mid] : (sorted[mid - 1] + sorted[mid]) / 2;
    setHistory('Median (Nilai Tengah)');
    setResult(median.toFixed(4).replace(/\.?0+$/, ''));
  };

  const calcMode = () => {
    handleTouch();
    if (dataset.length === 0) return setResult('Data Kosong');
    const counts = {};
    let maxCount = 0;
    dataset.forEach((num) => {
      counts[num] = (counts[num] || 0) + 1;
      if (counts[num] > maxCount) maxCount = counts[num];
    });
    const modes = Object.keys(counts).filter((num) => counts[num] === maxCount);
    setHistory('Modus (Nilai Sering Muncul)');
    setResult(modes.join(', '));
  };

  const calcVariance = () => {
    handleTouch();
    if (dataset.length < 2) return setResult('Butuh > 1 Data');
    const mean = dataset.reduce((a, b) => a + b, 0) / dataset.length;
    const variance = dataset.reduce((a, b) => a + Math.pow(b - mean, 2), 0) / (dataset.length - 1);
    setHistory('Varians (Sampel)');
    setResult(variance.toFixed(4).replace(/\.?0+$/, ''));
  };

  const calcStdDev = () => {
    handleTouch();
    if (dataset.length < 2) return setResult('Butuh > 1 Data');
    const mean = dataset.reduce((a, b) => a + b, 0) / dataset.length;
    const variance = dataset.reduce((a, b) => a + Math.pow(b - mean, 2), 0) / (dataset.length - 1);
    const stdDev = Math.sqrt(variance);
    setHistory('Simpangan Baku (Sampel)');
    setResult(stdDev.toFixed(4).replace(/\.?0+$/, ''));
  };

  const calcMinMax = () => {
    handleTouch();
    if (dataset.length === 0) return setResult('Data Kosong');
    const min = Math.min(...dataset);
    const max = Math.max(...dataset);
    setHistory('Min | Max');
    setResult(`${min} | ${max}`);
  };

  // Komponen Tombol yang bisa Mengambang (Floating Effect)
  const Btn = ({ label, onClick, className = "", colorClass = "bg-gray-100 text-gray-800" }) => (
    <button
      onClick={onClick}
      className={`
        relative overflow-hidden font-bold text-lg sm:text-xl rounded-2xl shadow-[0_5px_15px_-3px_rgba(0,0,0,0.1)]
        transition-all duration-300 ease-out select-none
        hover:-translate-y-1 hover:shadow-[0_8px_20px_-3px_rgba(0,0,0,0.2)] hover:scale-105
        active:-translate-y-3 active:scale-110 active:shadow-[0_15px_25px_-3px_rgba(0,100,255,0.4)]
        active:text-blue-600
        ${colorClass} ${className}
      `}
      style={{ touchAction: 'manipulation' }}
    >
      {label}
    </button>
  );

  return (
    <div className="min-h-screen bg-gray-900 flex items-center justify-center p-4 font-sans selection:bg-none">
      {/* Casing Calculator (Modern Klasik) */}
      <div className="bg-[#e0e5ec] w-full max-w-sm rounded-[2rem] p-6 shadow-[20px_20px_60px_#bebebe,-20px_-20px_60px_#ffffff] border border-gray-200">
        
        {/* Layar (Gaya CLI / Terminal Modern) */}
        <div className="bg-gray-900 rounded-xl p-4 mb-6 shadow-inner border-4 border-gray-300 relative overflow-hidden h-40 flex flex-col justify-between">
          <div className="absolute inset-0 bg-green-500 opacity-5 pointer-events-none"></div>
          
          {/* Dataset Display */}
          <div className="text-green-400 font-mono text-xs sm:text-sm h-10 overflow-y-auto break-all opacity-80 leading-tight">
            Data: [{dataset.join(', ')}]
          </div>
          
          {/* History / Info */}
          <div className="text-green-300 font-mono text-xs text-right mt-1 opacity-70">
            {history}
          </div>

          {/* Main Input / Result */}
          <div className="text-green-400 font-mono text-3xl sm:text-4xl text-right font-bold tracking-widest overflow-hidden whitespace-nowrap text-ellipsis">
            {result !== '' ? result : (currentInput || '0')}
            {result === '' && <span className="animate-pulse">_</span>}
          </div>
        </div>

        {/* Keypad Grid */}
        <div className="grid grid-cols-4 gap-3 sm:gap-4">
          
          {/* Baris Statistik Khusus */}
          <Btn label="Mean" onClick={calcMean} colorClass="bg-blue-100 text-blue-800 text-sm" />
          <Btn label="Med" onClick={calcMedian} colorClass="bg-blue-100 text-blue-800 text-sm" />
          <Btn label="Mod" onClick={calcMode} colorClass="bg-blue-100 text-blue-800 text-sm" />
          <Btn label="Var" onClick={calcVariance} colorClass="bg-blue-100 text-blue-800 text-sm" />
          
          <Btn label="Std" onClick={calcStdDev} colorClass="bg-blue-100 text-blue-800 text-sm" />
          <Btn label="Rng" onClick={calcMinMax} colorClass="bg-blue-100 text-blue-800 text-sm" />
          <Btn label="DEL" onClick={deleteLast} colorClass="bg-red-100 text-red-600" />
          <Btn label="AC" onClick={clearAll} colorClass="bg-red-500 text-white shadow-red-200" />

          {/* Baris Angka */}
          <Btn label="7" onClick={() => inputNumber('7')} />
          <Btn label="8" onClick={() => inputNumber('8')} />
          <Btn label="9" onClick={() => inputNumber('9')} />
          <Btn label="ADD" onClick={addData} className="col-start-4 row-span-2" colorClass="bg-green-500 text-white shadow-green-200" />

          <Btn label="4" onClick={() => inputNumber('4')} />
          <Btn label="5" onClick={() => inputNumber('5')} />
          <Btn label="6" onClick={() => inputNumber('6')} />

          <Btn label="1" onClick={() => inputNumber('1')} />
          <Btn label="2" onClick={() => inputNumber('2')} />
          <Btn label="3" onClick={() => inputNumber('3')} />
          <Btn label="=" onClick={calcMean} className="col-start-4 row-span-2" colorClass="bg-yellow-400 text-yellow-900 shadow-yellow-200" />

          <Btn label="0" onClick={() => inputNumber('0')} className="col-span-2" />
          <Btn label="." onClick={() => inputNumber('.')} />
          
        </div>
      </div>
    </div>
  );
}

```
