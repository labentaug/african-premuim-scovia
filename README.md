<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>African Scovia | Premium African Fashion Marketplace</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    
    <!-- Firebase SDK -->
    <script src="https://www.gstatic.com/firebasejs/9.22.2/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.2/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.2/firebase-firestore-compat.js"></script>
    
    <style>
        /* ========== PREMIUM COLOR SYSTEM ========== */
        :root {
            /* Primary - Rich Terracotta & Earth Tones */
            --primary-1: #C4452C;
            --primary-2: #B53B23;
            --primary-3: #9B2F1A;
            --primary-light: #FEE9E3;
            --primary-gradient: linear-gradient(135deg, #C4452C 0%, #E67E3B 100%);
            
            /* Secondary - Deep Indigo & Gold Accents */
            --secondary-1: #2C3E50;
            --secondary-2: #1A2A3A;
            --accent-gold: #D4AF37;
            --accent-gold-light: #F3E5AB;
            --accent-amber: #F39C12;
            
            /* Neutrals - Warm & Sophisticated */
            --bg-dark: #1E2A32;
            --bg-light: #FFFBF7;
            --bg-card: #FFFFFF;
            --text-dark: #1F2A3A;
            --text-muted: #5A6E7A;
            --text-light: #8A9AA8;
            --border-light: #F0E5DC;
            --border-medium: #E5D5C8;
            
            /* Shadows - Depth & Elegance */
            --shadow-sm: 0 2px 8px rgba(0,0,0,0.04);
            --shadow-md: 0 8px 24px rgba(0,0,0,0.08);
            --shadow-lg: 0 16px 40px rgba(0,0,0,0.12);
            --shadow-hover: 0 20px 35px -12px rgba(196,69,44,0.2);
            
            /* Gradients */
            --gradient-warm: linear-gradient(135deg, #C4452C 0%, #E67E3B 100%);
            --gradient-gold: linear-gradient(135deg, #D4AF37 0%, #F3E5AB 100%);
            --gradient-dark: linear-gradient(135deg, #1E2A32 0%, #2C3E50 100%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, sans-serif;
            background: var(--bg-light);
            color: var(--text-dark);
            line-height: 1.5;
            overflow-x: hidden;
        }

        /* ========== CUSTOM SCROLLBAR ========== */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: var(--border-light);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--primary-1);
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--primary-2);
        }

        /* ========== TYPOGRAPHY ========== */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

        h1, h2, h3, h4, .logo {
            font-family: 'Inter', sans-serif;
            letter-spacing: -0.02em;
        }

        /* ========== TOP BAR ========== */
        .top-bar {
            background: var(--secondary-1);
            color: rgba(255,255,255,0.85);
            padding: 10px 0;
            font-size: 13px;
            position: relative;
            z-index: 1001;
        }
        .top-container {
            max-width: 1440px;
            margin: 0 auto;
            padding: 0 32px;
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 12px;
        }
        .top-links a {
            color: rgba(255,255,255,0.75);
            text-decoration: none;
            margin-left: 28px;
            transition: all 0.3s ease;
            font-weight: 500;
        }
        .top-links a:hover {
            color: var(--accent-gold);
        }

        /* ========== MAIN NAVIGATION ========== */
        .navbar {
            background: var(--bg-card);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid var(--border-light);
        }
        .nav-container {
            max-width: 1440px;
            margin: 0 auto;
            padding: 16px 32px;
            display: flex;
            align-items: center;
            gap: 32px;
            flex-wrap: wrap;
        }
        .logo a {
            font-size: 1.8rem;
            font-weight: 800;
            text-decoration: none;
            background: var(--gradient-warm);
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -0.02em;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .logo i {
            background: var(--gradient-warm);
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-size: 1.6rem;
        }
        .logo small {
            font-size: 0.7rem;
            display: block;
            color: var(--text-muted);
            -webkit-text-fill-color: var(--text-muted);
            font-weight: 400;
            letter-spacing: normal;
        }
        .search-bar {
            flex: 1;
            max-width: 550px;
            display: flex;
        }
        .search-bar input {
            flex: 1;
            padding: 14px 22px;
            border: 2px solid var(--border-medium);
            border-right: none;
            border-radius: 50px 0 0 50px;
            font-size: 14px;
            transition: all 0.3s ease;
            background: var(--bg-card);
        }
        .search-bar input:focus {
            outline: none;
            border-color: var(--primary-1);
            box-shadow: 0 0 0 3px rgba(196,69,44,0.1);
        }
        .search-bar button {
            padding: 14px 28px;
            background: var(--gradient-warm);
            color: white;
            border: none;
            border-radius: 0 50px 50px 0;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        .search-bar button:hover {
            transform: translateX(2px);
            filter: brightness(1.05);
        }
        .nav-icons {
            display: flex;
            gap: 28px;
        }
        .nav-icon {
            text-align: center;
            text-decoration: none;
            color: var(--text-dark);
            position: relative;
            cursor: pointer;
            background: none;
            border: none;
            font-size: 13px;
            font-weight: 500;
            transition: color 0.3s ease;
        }
        .nav-icon:hover {
            color: var(--primary-1);
        }
        .nav-icon i {
            font-size: 1.5rem;
            display: block;
            margin-bottom: 5px;
        }
        .cart-count, .wishlist-count {
            position: absolute;
            top: -8px;
            right: -12px;
            background: var(--gradient-warm);
            color: white;
            border-radius: 50%;
            padding: 2px 7px;
            font-size: 10px;
            font-weight: bold;
            min-width: 20px;
        }

        /* ========== CATEGORY MENU ========== */
        .category-menu {
            background: var(--bg-card);
            border-bottom: 1px solid var(--border-light);
            overflow-x: auto;
            position: relative;
            z-index: 99;
        }
        .category-container {
            max-width: 1440px;
            margin: 0 auto;
            padding: 0 32px;
            display: flex;
            gap: 36px;
        }
        .category-container a {
            padding: 14px 0;
            text-decoration: none;
            color: var(--text-dark);
            font-weight: 600;
            white-space: nowrap;
            font-size: 14px;
            transition: all 0.3s ease;
            position: relative;
        }
        .category-container a:hover {
            color: var(--primary-1);
        }
        .category-container a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--gradient-warm);
            transition: width 0.3s ease;
        }
        .category-container a:hover::after {
            width: 100%;
        }

        /* ========== HERO BANNER ========== */
        .hero-banner {
            background: var(--gradient-dark);
            margin: 24px 32px;
            border-radius: 32px;
            padding: 48px 56px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 32px;
            position: relative;
            overflow: hidden;
        }
        .hero-banner::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -20%;
            width: 400px;
            height: 400px;
            background: radial-gradient(circle, rgba(212,175,55,0.1) 0%, transparent 70%);
            border-radius: 50%;
        }
        .hero-content h1 {
            font-size: 2.5rem;
            font-weight: 800;
            color: white;
            margin-bottom: 16px;
        }
        .hero-content p {
            color: rgba(255,255,255,0.8);
            margin-bottom: 28px;
            font-size: 1rem;
        }
        .hero-btn {
            background: var(--gradient-warm);
            color: white;
            padding: 14px 32px;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .hero-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(196,69,44,0.3);
        }
        .hero-stats {
            display: flex;
            gap: 48px;
            background: rgba(255,255,255,0.1);
            padding: 24px 36px;
            border-radius: 24px;
            backdrop-filter: blur(10px);
        }
        .stat-item {
            text-align: center;
        }
        .stat-number {
            font-size: 2rem;
            font-weight: 800;
            color: var(--accent-gold);
        }
        .stat-label {
            font-size: 12px;
            color: rgba(255,255,255,0.7);
        }

        /* ========== FLASH SALE ========== */
        .flash-sale {
            background: var(--gradient-warm);
            margin: 24px 32px;
            padding: 20px 32px;
            border-radius: 24px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
            box-shadow: var(--shadow-md);
        }
        .flash-sale-content {
            display: flex;
            align-items: center;
            gap: 16px;
        }
        .flash-sale-content i {
            font-size: 28px;
        }
        .timer {
            display: flex;
            gap: 12px;
            font-size: 1.6rem;
            font-weight: 800;
        }
        .timer span {
            background: rgba(0,0,0,0.25);
            padding: 8px 16px;
            border-radius: 16px;
            font-family: monospace;
        }

        /* ========== MAIN LAYOUT ========== */
        .main-layout {
            max-width: 1440px;
            margin: 24px auto;
            padding: 0 32px;
            display: grid;
            grid-template-columns: 280px 1fr;
            gap: 32px;
        }

        /* ========== SIDEBAR ========== */
        .sidebar {
            background: var(--bg-card);
            padding: 28px;
            border-radius: 28px;
            height: fit-content;
            position: sticky;
            top: 100px;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--border-light);
        }
        .filter-section {
            margin-bottom: 32px;
            border-bottom: 1px solid var(--border-light);
            padding-bottom: 24px;
        }
        .filter-section h4 {
            margin-bottom: 18px;
            color: var(--primary-1);
            font-size: 16px;
            font-weight: 700;
        }
        .price-range {
            width: 100%;
            margin: 12px 0;
            accent-color: var(--primary-1);
        }
        .filter-checkbox {
            display: block;
            margin: 12px 0;
            cursor: pointer;
            font-size: 14px;
        }
        .filter-checkbox input {
            margin-right: 12px;
            accent-color: var(--primary-1);
            width: 16px;
            height: 16px;
        }
        .btn-filter {
            background: var(--gradient-warm);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 50px;
            width: 100%;
            cursor: pointer;
            font-weight: 600;
            margin-top: 16px;
            transition: all 0.3s ease;
        }
        .btn-filter:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-sm);
        }
        .btn-reset {
            background: var(--bg-light);
            color: var(--text-dark);
            border: 1px solid var(--border-medium);
            padding: 12px;
            border-radius: 50px;
            width: 100%;
            cursor: pointer;
            margin-top: 12px;
            transition: all 0.3s ease;
            font-weight: 500;
        }
        .btn-reset:hover {
            border-color: var(--primary-1);
            color: var(--primary-1);
        }

        /* ========== PRODUCT GRID ========== */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 28px;
        }
        .product-card {
            background: var(--bg-card);
            border-radius: 24px;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            position: relative;
            cursor: pointer;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--border-light);
        }
        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: var(--shadow-hover);
        }
        .discount-badge {
            position: absolute;
            top: 16px;
            left: 16px;
            background: var(--primary-1);
            color: white;
            padding: 5px 12px;
            border-radius: 50px;
            font-size: 12px;
            font-weight: 700;
            z-index: 2;
        }
        .wishlist-btn {
            position: absolute;
            top: 16px;
            right: 16px;
            background: var(--bg-card);
            border: none;
            border-radius: 50%;
            width: 38px;
            height: 38px;
            cursor: pointer;
            z-index: 2;
            box-shadow: var(--shadow-sm);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .wishlist-btn:hover {
            transform: scale(1.1);
        }
        .product-card img {
            width: 100%;
            height: 260px;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        .product-card:hover img {
            transform: scale(1.05);
        }
        .product-info {
            padding: 20px;
        }
        .product-name {
            font-weight: 700;
            margin-bottom: 6px;
            font-size: 16px;
        }
        .seller-name {
            font-size: 12px;
            color: var(--text-muted);
            margin-bottom: 8px;
        }
        .rating {
            color: var(--accent-gold);
            font-size: 13px;
            margin-bottom: 10px;
        }
        .price {
            font-size: 1.4rem;
            font-weight: 800;
            color: var(--primary-1);
        }
        .old-price {
            text-decoration: line-through;
            color: var(--text-light);
            font-size: 0.85rem;
            margin-left: 10px;
            font-weight: normal;
        }
        .btn-add {
            width: 100%;
            padding: 12px;
            background: var(--gradient-warm);
            color: white;
            border: none;
            border-radius: 50px;
            margin-top: 16px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        .btn-add:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-sm);
        }

        /* ========== MODAL ========== */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.75);
            backdrop-filter: blur(8px);
            z-index: 2000;
            justify-content: center;
            align-items: center;
            animation: fadeIn 0.3s ease;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .modal-content {
            background: var(--bg-card);
            max-width: 1000px;
            width: 90%;
            border-radius: 32px;
            padding: 0;
            max-height: 85vh;
            overflow-y: auto;
            position: relative;
            animation: slideUp 0.4s ease;
        }
        @keyframes slideUp {
            from {
                transform: translateY(40px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        .modal-header {
            position: sticky;
            top: 0;
            background: var(--bg-card);
            padding: 24px 28px;
            border-bottom: 1px solid var(--border-light);
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 10;
        }
        .modal-header h2 {
            font-size: 1.5rem;
            color: var(--primary-1);
        }
        .close-modal {
            background: none;
            border: none;
            font-size: 28px;
            cursor: pointer;
            color: var(--text-muted);
            transition: all 0.3s ease;
            width: 44px;
            height: 44px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .close-modal:hover {
            background: var(--bg-light);
            color: var(--primary-1);
            transform: rotate(90deg);
        }
        .modal-body {
            padding: 28px;
        }

        /* ========== AUTH FORMS ========== */
        .auth-form {
            max-width: 500px;
            margin: 60px auto;
            padding: 48px;
            background: var(--bg-card);
            border-radius: 32px;
            box-shadow: var(--shadow-lg);
        }
        .auth-form h2 {
            text-align: center;
            color: var(--primary-1);
            margin-bottom: 36px;
            font-size: 28px;
        }
        .form-group {
            margin-bottom: 24px;
        }
        .form-group label {
            display: block;
            margin-bottom: 10px;
            font-
