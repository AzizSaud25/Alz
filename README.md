# Alz
// أدخل نتائج آخر الجولات يدويًا هنا (crash multipliers)
const recentCrashes = [1.2, 1.4, 2.5, 3.1, 1.1, 2.9, 5.0, 1.3, 1.7, 1.9];

// الدالة الذكية لتحديد الكاش أوت
function smartCashout(crashes) {
  const avg = crashes.reduce((a, b) => a + b, 0) / crashes.length;
  const maxCrash = Math.max(...crashes);

  if (maxCrash > 50) {
    return 1.3; // بعد جولة مرتفعة جدًا، غالبًا فيه كراش مبكر
  } else if (avg < 2) {
    return 1.35; // السوق ضعيف، خروج مبكر
  } else if (avg < 3) {
    return 2.0; // سوق متوازن
  } else {
    return 2.5; // السوق جيد، هدف أعلى
  }
}

// الحصول على التوصية
const suggestedCashout = smartCashout(recentCrashes);
console.log(`اقتراح Auto Cashout: ${suggestedCashout}x`);