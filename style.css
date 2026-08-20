// ===== 禁用右键菜单 =====
document.addEventListener('contextmenu', (e) => {
    e.preventDefault();
});

// ===== 禁用图片拖拽下载 =====
document.addEventListener('dragstart', (e) => {
    if (e.target.tagName === 'IMG') {
        e.preventDefault();
    }
});

// ===== 禁止保存图片快捷键 =====
document.addEventListener('keydown', (e) => {
    // 禁止 Ctrl+S / Cmd+S 保存页面
    if ((e.ctrlKey || e.metaKey) && e.key === 's') {
        e.preventDefault();
    }
    // 禁止 Alt+图片保存
    if (e.altKey && (e.key === 'ArrowLeft' || e.key === 'ArrowRight')) {
        e.preventDefault();
    }
});

// ===== 打开抖音APP =====
function openDouyin(e) {
    e.preventDefault();
    const appUrl = 'aweme://';
    const webUrl = 'https://www.douyin.com/user/self?from_tab_name=main';
    
    // 尝试打开APP
    const startTime = Date.now();
    const timer = setTimeout(() => {
        // 如果3秒内页面没有隐藏，说明没安装APP，跳转网页版
        if (Date.now() - startTime < 3500) {
            window.location.href = webUrl;
        }
    }, 2500);
    
    // 监听页面隐藏来清除定时器
    window.addEventListener('pagehide', () => clearTimeout(timer));
    window.addEventListener('blur', () => clearTimeout(timer));
    
    window.location.href = appUrl;
    
    // 重置定时器（因为跳转成功后定时器会触发，但页面已隐藏）
    setTimeout(() => {
        clearTimeout(timer);
    }, 500);
}

// ===== 复制邮箱 =====
function copyEmail(e, email) {
    e.preventDefault();
    navigator.clipboard.writeText(email).then(() => {
        const hint = document.getElementById('copyHint');
        hint.textContent = '✓ 邮箱已复制到剪贴板：' + email;
        hint.style.color = '#8b6f47';
        setTimeout(() => {
            hint.textContent = '点击邮箱可复制邮箱地址';
            hint.style.color = '';
        }, 3000);
    }).catch(() => {
        // 兼容旧浏览器
        const textarea = document.createElement('textarea');
        textarea.value = email;
        document.body.appendChild(textarea);
        textarea.select();
        document.execCommand('copy');
        document.body.removeChild(textarea);
        
        const hint = document.getElementById('copyHint');
        hint.textContent = '✓ 邮箱已复制：' + email;
        hint.style.color = '#8b6f47';
        setTimeout(() => {
            hint.textContent = '点击邮箱可复制邮箱地址';
            hint.style.color = '';
        }, 3000);
    });
}

// ===== 首屏图片轮播 =====
const slides = document.querySelectorAll('.hero-slide');
let currentSlide = 0;

function nextSlide() {
    slides[currentSlide].classList.remove('active');
    currentSlide = (currentSlide + 1) % slides.length;
    slides[currentSlide].classList.add('active');
}

// 每3.3秒切换一次
setInterval(nextSlide, 2500);

// ===== 导航栏 =====
const navbar = document.getElementById('mainNav');

// ===== 首屏欢迎页：点击开始按钮后消失 =====
const welcomePage = document.getElementById('welcomePage');
const startBtn = document.getElementById('startBtn');
const mainNav = document.getElementById('mainNav');

// 欢迎页显示时禁止滚动
document.body.style.overflow = 'hidden';

startBtn.addEventListener('click', () => {
    // 淡出欢迎页
    welcomePage.classList.add('hidden');
    
    // 允许滚动
    document.body.style.overflow = '';
    
    // 显示导航栏并滚动到关于Laufey
    setTimeout(() => {
        mainNav.classList.add('visible');
        const aboutSection = document.getElementById('about');
        if (aboutSection) {
            const navHeight = mainNav.offsetHeight;
            const targetPosition = aboutSection.getBoundingClientRect().top + window.pageYOffset - navHeight + 50;
            window.scrollTo({
                top: targetPosition,
                behavior: 'smooth'
            });
        }
    }, 400);
});

// ===== 导航栏滚动效果 =====
window.addEventListener('scroll', () => {
    if (window.scrollY > 50) {
        navbar.classList.add('scrolled');
    } else {
        navbar.classList.remove('scrolled');
    }
});

// ===== 平滑滚动 =====
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const targetHref = this.getAttribute('href');
        
        // 如果是logo链接（回到顶部）
        if (targetHref === '#') {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
            return;
        }
        
        const target = document.querySelector(targetHref);
        if (target) {
            const navHeight = navbar.offsetHeight;
            const targetPosition = target.getBoundingClientRect().top + window.pageYOffset - navHeight + 50;
            window.scrollTo({
                top: targetPosition,
                behavior: 'smooth'
            });
        }
    });
});

// ===== 滚动渐入动画 =====
const observerOptions = {
    threshold: 0.15,
    rootMargin: '0px 0px -50px 0px'
};

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
        }
    });
}, observerOptions);

// 为各板块添加淡入效果
document.querySelectorAll('.section-header, .about-content, .disc-item, .gallery-item, .contact-content').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(30px)';
    el.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
    observer.observe(el);
});

// ===== 专辑详情交互 =====
const albumData = {
    'from-the-start': {
        title: 'Typical of Me',
        year: '2021',
        cover: 'images/typical-of-me.jpg',
        tracks: [
            { title: 'Street by Street', duration: '3:30' },
            { title: 'Magnolia', duration: '3:18' },
            { title: 'Like The Movies', duration: '3:22' },
            { title: 'I Wish You Love', duration: '3:13' },
            { title: 'James', duration: '3:40' },
            { title: 'Someone New', duration: '3:18' },
            { title: 'Best Friend', duration: '3:01' }
        ]
    },
    'valentine': {
        title: 'Everything I Know About Love',
        year: '2022',
        cover: 'images/everything-i-know-about-love.jpg',
        tracks: [
            { title: 'Valentine', duration: '3:17' },
            { title: 'Falling Behind', duration: '2:53' },
            { title: 'Dreamer', duration: '3:35' },
            { title: 'Fragile', duration: '3:40' },
            { title: 'Like the Movies', duration: '3:21' },
            { title: 'Dear Soulmate', duration: '3:02' },
            { title: 'What Love Will Do to You', duration: '2:50' },
            { title: "I've Never Been in Love Before", duration: '3:02' },
            { title: 'Dance With You Tonight', duration: '3:01' },
            { title: 'Night Light', duration: '2:54' },
            { title: 'Slow Down', duration: '3:34' },
            { title: 'No String Attached', duration: '3:24' }
        ]
    },
    'bewitched': {
        title: 'Bewitched',
        year: '2023',
        cover: 'images/bewitched.jpg',
        tracks: [
            { title: 'Dreamer', duration: '3:30' },
            { title: 'Second Best', duration: '3:24' },
            { title: 'Haunted', duration: '3:20' },
            { title: 'Must Be Love', duration: '3:04' },
            { title: 'While You Were Sleeping', duration: '2:57' },
            { title: 'Lovesick', duration: '3:45' },
            { title: 'California and Me', duration: '3:36' },
            { title: 'Nocturne (Interlude)', duration: '2:24' },
            { title: 'Promise', duration: '3:54' },
            { title: 'From The Start', duration: '2:49' },
            { title: 'Misty', duration: '3:29' },
            { title: 'Serendipity', duration: '3:39' },
            { title: 'Letter To My 13 Year Old Self', duration: '4:22' },
            { title: 'Bewitched', duration: '4:06' }
        ]
    },
    'a-matter-of-time': {
        title: 'A Matter Of Time',
        year: '2025',
        cover: 'images/a-matter-of-time.jpg',
        tracks: [
            { title: 'Clockwork', duration: '2:30' },
            { title: 'Lover Girl', duration: '2:44' },
            { title: 'Snow White', duration: '3:13' },
            { title: 'Castle in Hollywood', duration: '2:33' },
            { title: 'Carousel', duration: '3:19' },
            { title: 'Silver Lining', duration: '3:17' },
            { title: 'Too Little, Too Late', duration: '3:53' },
            { title: 'Cuckoo Ballet (Interlude)', duration: '3:39' },
            { title: 'Forget-Me-Not', duration: '4:06' },
            { title: 'Tough Luck', duration: '3:12' },
            { title: 'A Cautionary Tale', duration: '4:16' },
            { title: 'Mr. Eclectic', duration: '2:35' },
            { title: 'Clean Air', duration: '2:35' },
            { title: 'Sabotage', duration: '3:34' }
        ]
    },
    'the-final-hour': {
        title: 'A Matter Of Time: The Final Hour',
        year: '2026',
        cover: 'images/the-final-hour.jpg',
        tracks: [
            { title: 'Clockwork', duration: '2:30' },
            { title: 'Lover Girl', duration: '2:44' },
            { title: 'Snow White', duration: '3:13' },
            { title: 'Castle in Hollywood', duration: '2:33' },
            { title: 'Carousel', duration: '3:19' },
            { title: 'Silver Lining', duration: '3:17' },
            { title: 'Too Little, Too Late', duration: '3:53' },
            { title: 'Cuckoo Ballet (Interlude)', duration: '3:39' },
            { title: 'Forget-Me-Not', duration: '4:06' },
            { title: 'Tough Luck', duration: '3:12' },
            { title: 'A Cautionary Tale', duration: '4:16' },
            { title: 'Mr. Eclectic', duration: '2:35' },
            { title: 'Clean Air', duration: '2:35' },
            { title: 'Sabotage', duration: '3:34' },
            { title: 'Seems Like Old Times', duration: '3:28' },
            { title: 'Madwoman', duration: '3:22' },
            { title: 'How I Get', duration: '3:11' },
            { title: 'I Wait, I Wait, I Wait', duration: '3:41' },
            { title: "I'll Forget About You (In Time)", duration: '3:36' }
        ]
    }
};

const albumDetail = document.getElementById('albumDetail');
const backBtn = document.getElementById('backBtn');
const albumCoverLarge = document.getElementById('albumCoverLarge');
const albumTitle = document.getElementById('albumTitle');
const albumYear = document.getElementById('albumYear');
const trackList = document.getElementById('trackList');

document.querySelectorAll('.disc-item').forEach(item => {
    item.addEventListener('click', () => {
        const albumId = item.dataset.album;
        const data = albumData[albumId];
        if (!data) return;
        
        albumCoverLarge.style.backgroundImage = `url('${data.cover}')`;
        albumTitle.textContent = data.title;
        albumYear.textContent = data.year;
        
        trackList.innerHTML = data.tracks.map((track, i) => `
            <li>
                <span class="track-number">${String(i + 1).padStart(2, '0')}</span>
                <span class="track-title">${track.title}</span>
                <span class="track-duration">${track.duration}</span>
            </li>
        `).join('');
        
        albumDetail.classList.add('active');
        document.body.style.overflow = 'hidden';
    });
});

backBtn.addEventListener('click', () => {
    albumDetail.classList.remove('active');
    document.body.style.overflow = '';
});

// ===== 相册点击放大（简单灯箱效果）====
const galleryItems = document.querySelectorAll('.gallery-item');
let lightbox = null;

galleryItems.forEach(item => {
    item.addEventListener('click', () => {
        const imgSrc = item.querySelector('img').src;
        createLightbox(imgSrc);
    });
});

function createLightbox(src) {
    // 创建灯箱
    lightbox = document.createElement('div');
    lightbox.style.cssText = `
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 9999;
        cursor: pointer;
        animation: fadeIn 0.3s ease;
    `;
    
    // 创建返回按钮
    const backBtn = document.createElement('div');
    backBtn.style.cssText = `
        position: absolute;
        top: 30px;
        left: 30px;
        width: 40px;
        height: 40px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.3);
        backdrop-filter: blur(10px);
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: all 0.3s ease;
        z-index: 10000;
    `;
    backBtn.innerHTML = '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"></polyline></svg>';
    backBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        closeLightbox();
    });
    
    const img = document.createElement('img');
    img.src = src;
    img.style.cssText = `
        max-width: 90%;
        max-height: 90%;
        object-fit: contain;
        border-radius: 8px;
        box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    `;
    
    lightbox.appendChild(backBtn);
    lightbox.appendChild(img);
    document.body.appendChild(lightbox);
    
    lightbox.addEventListener('click', closeLightbox);
    document.addEventListener('keydown', (e) => {
        if (e.key === 'Escape') closeLightbox();
    });
}

function closeLightbox() {
    if (lightbox) {
        if (lightbox.parentNode) {
            lightbox.parentNode.removeChild(lightbox);
        }
        lightbox = null;
    }
}

// ===== 导航链接激活状态 =====
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-link');

window.addEventListener('scroll', () => {
    let current = '';
    const scrollPosition = window.scrollY + 100;
    
    sections.forEach(section => {
        const sectionTop = section.offsetTop;
        const sectionHeight = section.offsetHeight;
        if (scrollPosition >= sectionTop && scrollPosition < sectionTop + sectionHeight) {
            current = section.getAttribute('id');
        }
    });
    
    navLinks.forEach(link => {
        link.style.color = '';
        if (link.getAttribute('href') === '#' + current) {
            link.style.color = 'var(--color-accent)';
        }
    });
});
