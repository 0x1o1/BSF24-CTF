# BSF24-CTF
رايت أب لتحديات م.فيصل الحميد في مجال الفريق الدفاعي بمجموع (21) تحدي في مجالات مثل ( التحقيق الجنائي الرقمي , تحليل السجلات(Logs) , تحليل الشبكة  , الذكاء مفتوح المصدر (Osint) , إخفاء البيانات (stegnography) , ذكاء المخاطر(Threat Intelligence))

أولاً خلونا نبدأ بأول تحدي وهو بكل بساطة مدخل للموقع المقامة عليه باقي التحديات:
# إسم التحدي : Start Here
التحدي بكل بساطة ترحيب في بالموقع و هدية أول (50) نقطة.

![Flag1](https://github.com/0x1o1/BSF24-CTF/assets/112539392/61c5594b-1b51-4196-924f-873640b2b257)

الفلاق : FlagBSF{BSF_CTF_2024}

# أول مجال راح نشتغل عليه بالترتيب المنطقي هو مجال (تحليل السجلات - Logs Analysis) :
مكون من هالمجال 4 تحديات وكلها ترتبط في بعض والمطلوب منك عشان تحل التحديات حسب كل وصف لكل تحدي تحلل ملف الإكسل المرفق وتستخرج الحل على صيغة فلاق FlagBSF{example} :

![اسم الملف](https://github.com/0x1o1/BSF24-CTF/assets/112539392/53161d0a-8bf6-49e5-a6fa-6f943c37f13b)

# إسم التحدي : Failure 1
وصف التحدي : واحد من مدراء الأنظمة الخاصين بنا إكتشف أو تعرف على تصرف مشبوه في "سجلات الأمان - Security Logs" الخاصة بنظام ويندوز, ما هو "معرّف الحدث - event ID" المستخدم لمعرفة عملية تسجيل الدخول الفاشلة أو الخاطئة؟

![Log analysis](https://github.com/0x1o1/BSF24-CTF/assets/112539392/1a480cf8-713a-4703-9d45-def8ed2f3375)

هنا نبدأ نستخدم مخنا شوي طبعا فيه كلمة "فشل - failed" وطبعا فيه ملف إكسل فيه الكثير من البيانات ممكن أنا أختصر على نفسي و أستخدم البحث عن الكلمة بمعنى نفلتر الملف عشان أوجد المطلوب بأسرع ما يمكن فـ ممكن نستخدم "CTRL + F" ونلصق failed ونبحث عن الـ "المعرّف أو ID"
حجم البيانات بشكل نظري مرعب مستحيل احلل هذا كله بالشكل الطبيعي:

![حجم البيانات](https://github.com/0x1o1/BSF24-CTF/assets/112539392/87c2a8b7-9a01-4741-939b-e9b43c98b207)

لذلك أول شيء بعرف في أي خانة ممكن أحصل الـ ID؟ فـ عادة في كل ملف فوق في أول صف تعريف الخانات مثل اللي في الصورة :

![خانة 4](https://github.com/0x1o1/BSF24-CTF/assets/112539392/2c87f3bb-4675-45be-9723-22c26f69a337)

فـ عن طريق الصورة السابقة ممكن تعرف ان رابع خانة من كل صف بتكون محفوظة فيها قيمة الـ "EventID".
الآن جاء وقت إستخدام ال "CTRL + F" مع كلمة Failed عشان نطلع الفلاق:

![الفلاق تبعنا](https://github.com/0x1o1/BSF24-CTF/assets/112539392/910b42fa-de5b-42a6-83cd-a4cb0e85aea5)

بكل بساطة طلع لي كافة تفاصيل "الدخول الخاطئ - Failed login" ولو تلاحظون في رابع خانة الـ "EventID" مكون من 4 خانات (4625).

إذا حاب تعرف أكثر عن الـ "Event ID's" ممكن تزور موقع"MITRE ATT&CK : https://attack.mitre.org" وهو الموقع المعتمد لأي مختص فريق دفاعي كمرجع تقدر عن طريقة تكشف نوع الهجوم وهجوم الـ Failed كان هجوم "القوة الغاشمة - Brute force" حسب نوع الـ"EvenID" من صفحة الموقع الآتية : https://attack.mitre.org/techniques/T1110/003/

الفلاق : FlagBSF{4625}

# إسم التحدي : Failure 2
وصف التحدي : إكمالاً لـ"Failure 1", كم عدد مرات تسجيل الدخول الخاطئة لاحظت؟

![Failure2](https://github.com/0x1o1/BSF24-CTF/assets/112539392/7a611d86-fbb7-4727-979e-e745ac82fec6)
بكل بساطة نسوي نفس خطوات البحث اللي في التحدي الأول "CTRL + F" ونكتب "Failed" ونبحث راح يطلع لك اول عملية هنا تبدأ تحسب وتضغط "Enter" بمعنى أعطيني عملية الدخول الخاطئة اللي بعدها لو إستمريت و أنت تحسب بتكتشف إنها فقط 4 مرات تم رصدها في الملف وبكذا يكون عدد مرات الدخول الفاشلة 4.

الفلاق : FlagBSF{4}

# إسم التحدي : Failure 3
وصف التحدي : إكمالاً لـ"Failure 2", بناءً على عمليات تسجيل الدخول الخاطئة ماذا كان عنوان الـ"IP" المستخدم من قِبل المخترق لعملية تسجيل الدخول على الشبكة؟

![Failure3](https://github.com/0x1o1/BSF24-CTF/assets/112539392/3c7eee0d-360f-4c99-acd6-1bae520cc1ff)
نقدر نطلع الـ"IP" بكل سهولة بعد ما قدرنا نستخرج الـ"EventID" لأنه بكل بساطة معاه في نفس الصف ولا يوجد أي "IP" آخر.

![الاي بي](https://github.com/0x1o1/BSF24-CTF/assets/112539392/84ff68f6-16d7-4cf6-906c-d36096c61fb0)

الفلاق : FlagBSF{192.168.80.128}

# إسم التحدي : Failure 4
وصف التحدي : إكمالاً لـ"Failure 3", ما هو إسم المستخدم  المسؤول عن مسح السجلات؟

![Failure 4 chall](https://github.com/0x1o1/BSF24-CTF/assets/112539392/7d178106-5a5c-4da2-a856-3dd7aa0fdfe8)

بكل بساطة ممكن نبحث عن المستخدم بنفس السبل السابقة بإستخدام "Failed" في بحث ملف الإكسل ولكن كيف نميز اليوزر ذو الصلاحيات العالية؟ غالبًا بناء على صلاحياته ولا يمكن مسح السجلات عن طريق مستخدم عادي لذلك نبحث عن أي صلة لمستخدم بمسمى ذو صلاحيات عالية:
![admin](https://github.com/0x1o1/BSF24-CTF/assets/112539392/492eec5e-cb55-417d-a857-db6940ff741c)

نلاحظ أن مستخدم "Administrator" متعلق بعملية الدخول الخاطئة وبهذه الطريقة وجدنا المطلوب.
الفلاق : FlagBSF{administrator}

