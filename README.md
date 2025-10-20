# TensorFlow Playground - Digital Trendz Fork

![Digital Trendz](https://digital-trendz.net/logo.svg)

## 🎯 About This Repository

This is **Digital Trendz's** fork of the [TensorFlow Playground](https://github.com/tensorflow/playground) project, an interactive visualization tool for neural networks. We've contributed enhancements to this educational platform as part of our commitment to advancing Business Intelligence and AI technologies.

**Original Project**: [tensorflow/playground](https://github.com/tensorflow/playground)  
**Live Demo**: [playground.tensorflow.org](http://playground.tensorflow.org)

---

## 🚀 Our Contributions

### ✨ LeakyReLU Activation Function

We've implemented the **LeakyReLU activation function** to enhance the educational value of the playground:

**Features**:
- Prevents "dying ReLU" problem in neural networks
- Allows small gradient flow for negative values (0.01 slope)
- Educational comparison with standard ReLU
- Fully integrated into the UI

**Modified Files**:
- `src/nn.ts` - LeakyReLU implementation with derivative
- `src/state.ts` - State management registration
- `index.html` - UI dropdown integration

**Testing Status**: ✅ Tested with all datasets (Circle, XOR, Gaussian, Spiral)

---

## 🌟 About Digital Trendz

**Digital Trendz** is an enterprise-grade Business Intelligence consulting platform delivering data-driven solutions across 4 continents. Our mission is to **Re-define Business Intelligence** by transforming digital trends and data into original, innovative, and sustainable solutions.

### 🎯 Core Services

**Consulting Services**
- Business Intelligence - BI strategy, implementation, optimization
- Data Management - MDM, Data Governance, Data Quality
- Cloud & Infrastructure - Cloud migration, Big Data, Data Lakes
- Digital Transformation - Strategy, Process Optimization
- AI & Emerging Technologies - Machine Learning, Predictive Analytics, AI Agents

**Training & Development**
- Microsoft (Power BI, Azure, Power Platform)
- Informatica (PowerCenter, Cloud Integration, MDM)
- Tableau (Desktop, Server, Advanced Analytics)
- Databricks (Data Engineering, Apache Spark, ML)
- SAP (Analytics Cloud, BusinessObjects)

**Custom Solutions**
- Laibraries.com - AI-powered academic research workspace
- Mimogram.com - Digital marketing marketplace
- Tawasool.com - Next-gen social media ecosystem
- LegalDZ.com - Legal intelligence SaaS platform
- LocalEasy - B2B prospecting automation
- RoMarkt - Multi-service collaboration platform

---

## 🏢 Global Presence

**Headquarters - Algeria**
- 📍 01 Rue Ahmed OUAKED, Dely Brahim, Alger – Algeria
- 📞 (+213) 554 227 641
- 📧 bi@digital-trendz.net

**International Offices**
- 🇺🇸 **USA**: 201 Spear Street, Suite 1100, San Francisco, CA
- 🇫🇷 **France**: 60 Rue François 1er, 75008 Paris
- 🇷🇺 **Russia**: Yeysk, Krasnodar

**Website**: [www.digital-trendz.net](https://www.digital-trendz.net)

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18.17 or later
- npm or yarn package manager

### Installation

```bash
# Clone this repository
git clone https://github.com/dataswarmproject/playground.git
cd playground

# Install dependencies
npm install

# Run development server with auto-reload
npm run serve-watch
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

### Build for Production

```bash
# Create optimized production build
npm run build

# Serve production build
npm run serve
```

---

## 💻 Technology Stack

- **Language**: TypeScript 2.9
- **Visualization**: D3.js v3.5.16
- **UI Framework**: Material Design Lite v1.3.0
- **Build System**: Browserify + Uglify-js
- **Development**: Watchify + Concurrently

---

## 📖 Project Structure

```
playground/
├── src/
│   ├── playground.ts    # Main application logic
│   ├── nn.ts           # Neural network implementation ⭐ Modified
│   ├── state.ts        # State management ⭐ Modified
│   ├── dataset.ts      # Dataset generators
│   ├── heatmap.ts      # Heatmap visualization
│   └── linechart.ts    # Loss chart
├── index.html          # UI structure ⭐ Modified
├── styles.css          # Styling
├── dist/               # Build output
└── package.json        # Dependencies
```

---

## 🎓 Educational Features

### Activation Functions
- ReLU (Rectified Linear Unit)
- Tanh (Hyperbolic Tangent)
- Sigmoid
- Linear
- **LeakyReLU** ⭐ *New - Digital Trendz Contribution*

### Datasets
- Circle classification
- XOR pattern
- Gaussian clusters
- Spiral pattern
- Regression (Plane, Gaussian)

### Hyperparameters
- Learning rate adjustment
- Regularization (L1, L2)
- Batch size configuration
- Network architecture customization
- Noise level control

---

## 🤝 Contributing Back to TensorFlow Playground

This contribution will be submitted as a pull request to the original TensorFlow Playground repository:
1. Fork submitted: ✅
2. Code implemented: ✅
3. Testing completed: ✅
4. Pull request: 🔄 In progress
5. Google CLA signed: ⏳ Pending

---

## 📊 Key Statistics

**Digital Trendz Achievements**:
- ✅ **1000+** BI projects delivered
- ✅ **4** global offices (Algeria, USA, France, Russia)
- ✅ **50+** training courses available
- ✅ **6** custom platforms developed
- ✅ **100%** enterprise client satisfaction

**TensorFlow Playground**:
- ⭐ **12,600+** GitHub stars
- 🍴 **2,700+** forks
- 🌍 Used by students and educators worldwide
- 🎓 Featured in ML courses globally

---

## 🔐 Why We Contribute to Open Source

At **Digital Trendz**, we believe in:
- 🌍 **Knowledge Sharing** - Contributing to the global tech community
- 🎓 **Education** - Enhancing learning tools for future data scientists
- 💡 **Innovation** - Advancing AI and machine learning technologies
- 🤝 **Collaboration** - Working with world-class developers and researchers

Open source contributions are part of our commitment to **Re-defining Business Intelligence** and fostering innovation in the AI/ML ecosystem.

---

## 👨‍💼 Leadership

**Dr. Ahmed HALLOUB**  
*Founder & Chief Data Scientist*  
Business Intelligence PhD & Psychometrician

With over 1000+ successful BI projects and a presence across 4 continents, Dr. Halloub leads Digital Trendz in delivering cutting-edge data solutions and fostering technological innovation.

---

## 📞 Contact & Support

**For Business Inquiries**:
- 📧 Email: bi@digital-trendz.net
- 📞 Phone: (+213) 554 227 641
- 🌐 Website: [www.digital-trendz.net](https://www.digital-trendz.net)

**For Technical Issues**:
- Open an issue in this repository
- Reference the original [TensorFlow Playground issues](https://github.com/tensorflow/playground/issues)

---

## 📜 License

This project maintains the original **Apache License 2.0** from TensorFlow Playground.

**Original Work**: Copyright © 2016 Google Inc.  
**Contributions**: Copyright © 2025 Digital Trendz

See [LICENSE](LICENSE) for full details.

---

## 🙏 Acknowledgments

- **Google & TensorFlow Team** - For creating the original Playground
- **Daniel Smilkov & Shan Carter** - Original authors
- **Open Source Community** - For continuous improvements
- **Digital Trendz Team** - For the LeakyReLU contribution

---

## 🔗 Related Resources

### Digital Trendz Platforms
- [Laibraries.com](https://www.laibraries.com) - Academic research workspace
- [Mimogram.com](https://www.mimogram.com) - Digital marketing marketplace
- [Tawasool.com](https://www.tawasool.com) - Social media ecosystem
- [LegalDZ.com](https://www.legaldz.com) - Legal intelligence platform

### TensorFlow Resources
- [TensorFlow Official](https://www.tensorflow.org/)
- [TensorFlow Playground](http://playground.tensorflow.org)
- [TensorFlow GitHub](https://github.com/tensorflow)

### Learning Resources
- [Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/)
- [3Blue1Brown - Neural Networks](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi)
- [Deep Learning Specialization](https://www.coursera.org/specializations/deep-learning)

---

## 🎯 Future Contributions

We plan to continue contributing to TensorFlow Playground with:
- Additional activation functions (Swish, ELU, GELU)
- Advanced optimizers (Adam, RMSprop)
- New educational datasets
- Performance optimizations
- Enhanced visualizations

Stay tuned for more contributions from the Digital Trendz team! 🚀

---

<div align="center">

**Built with ❤️ by Digital Trendz**  
*Re-defining Business Intelligence, one project at a time.*

[![Website](https://img.shields.io/badge/Website-digital--trendz.net-blue)](https://www.digital-trendz.net)
[![Email](https://img.shields.io/badge/Email-bi@digital--trendz.net-red)](mailto:bi@digital-trendz.net)
[![GitHub](https://img.shields.io/badge/GitHub-dataswarmproject-black)](https://github.com/dataswarmproject)

**Original TensorFlow Playground**: [playground.tensorflow.org](http://playground.tensorflow.org)

</div>
