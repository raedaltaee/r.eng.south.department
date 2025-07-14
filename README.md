    <div id="auth-section" class="card text-sm text-gray-600 mb-6 flex justify-between items-center">
        <div>
            <p>مرحباً بك في النظام!</p>
            <p>معرف المستخدم الحالي: <span id="user-id" class="font-mono text-blue-600">جاري التحميل...</span></p>
            <p>حالة المصادقة: <span id="auth-status" class="font-semibold text-gray-700">جاري التحقق...</span></p>
        </div>
        <div>
            <button id="auth-button" class="btn btn-primary">تسجيل الدخول / البدء</button>
        </div>
    </div>

    <!-- Message Box -->
    <div id="messageBox" class="message-box"></div>

    <!-- Main Content - Hidden until authenticated -->
    <div id="main-content" class="hidden">
        <!-- Part 1: إدارة الكيانات الدينية والتعليمية -->
        <div class="mb-8">
            <h2 class="text-3xl font-bold text-gray-700 mb-6 text-center border-b-2 border-blue-500 pb-2">إدارة الكيانات الدينية والتعليمية</h2>

            <!-- Religious and Charitable Institutions Section -->
            <div class="card">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">المؤسسات الدينية والخيرية</h3>

                <form id="addInstitutionForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="institutionName" class="block text-gray-700 text-sm font-bold mb-2">اسم المؤسسة:</label>
                            <input type="text" id="institutionName" class="form-input" placeholder="اسم المؤسسة" required>
                        </div>
                        <div>
                            <label for="institutionType" class="block text-gray-700 text-sm font-bold mb-2">النوع:</label>
                            <select id="institutionType" class="form-input" required>
                                <option value="">اختر النوع</option>
                                <option value="جامع">جامع</option>
                                <option value="حسينية">حسينية</option>
                                <option value="مؤسسة خيرية">مؤسسة خيرية</option>
                            </select>
                        </div>
                        <div>
                            <label for="institutionGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="institutionGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div>
                            <label for="institutionLocation" class="block text-gray-700 text-sm font-bold mb-2">الموقع:</label>
                            <input type="text" id="institutionLocation" class="form-input" placeholder="الموقع" required>
                        </div>
                        <div class="md:col-span-2">
                            <label for="institutionCapacity" class="block text-gray-700 text-sm font-bold mb-2">القدرة الاستيعابية (تقريبًا):</label>
                            <input type="number" id="institutionCapacity" class="form-input" placeholder="القدرة الاستيعابية" min="0">
                        </div>

                        <!-- New Fields for Institutions -->
                        <div>
                            <label for="institutionEndowmentType" class="block text-gray-700 text-sm font-bold mb-2">نوع الوقف:</label>
                            <input type="text" id="institutionEndowmentType" class="form-input" placeholder="نوع الوقف">
                        </div>
                        <div class="md:col-span-2">
                            <label for="institutionArchitecturalStatus" class="block text-gray-700 text-sm font-bold mb-2">حالته العمرانية:</label>
                            <textarea id="institutionArchitecturalStatus" class="form-textarea" placeholder="وصف الحالة العمرانية"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="institutionObstacles" class="block text-gray-700 text-sm font-bold mb-2">العقبات:</label>
                            <textarea id="institutionObstacles" class="form-textarea" placeholder="العقبات التي تواجه المؤسسة"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="institutionNeeds" class="block text-gray-700 text-sm font-bold mb-2">الاحتياجات:</label>
                            <textarea id="institutionNeeds" class="form-textarea" placeholder="احتياجات المؤسسة"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="institutionSolutions" class="block text-gray-700 text-sm font-bold mb-2">الحلول المقترحة:</label>
                            <textarea id="institutionSolutions" class="form-textarea" placeholder="الحلول المقترحة للعقبات والاحتياجات"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة مؤسسة</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">المؤسسات الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>الاسم</th>
                                <th>النوع</th>
                                <th>المحافظة</th>
                                <th>الموقع</th>
                                <th>القدرة</th>
                                <th>نوع الوقف</th>
                                <th>الحالة العمرانية</th>
                                <th>العقبات</th>
                                <th>الاحتياجات</th>
                                <th>الحلول</th>
                            </tr>
                        </thead>
                        <tbody id="institutionsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Religious Education Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">التعليم الديني (المدارس)</h3>

                <form id="addSchoolForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="schoolName" class="block text-gray-700 text-sm font-bold mb-2">اسم المدرسة:</label>
                            <input type="text" id="schoolName" class="form-input" placeholder="اسم المدرسة" required>
                        </div>
                        <div>
                            <label for="schoolType" class="block text-gray-700 text-sm font-bold mb-2">النوع:</label>
                            <select id="schoolType" class="form-input" required>
                                <option value="">اختر النوع</option>
                                <option value="دينية">دينية</option>
                                <option value="عامة">عامة</option>
                            </select>
                        </div>
                        <div>
                            <label for="schoolGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="schoolGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div>
                            <label for="schoolLocation" class="block text-gray-700 text-sm font-bold mb-2">الموقع:</label>
                            <input type="text" id="schoolLocation" class="form-input" placeholder="الموقع" required>
                        </div>
                        <div>
                            <label for="studentPrimaryMale" class="block text-gray-700 text-sm font-bold mb-2">ذكور ابتدائي:</label>
                            <input type="number" id="studentPrimaryMale" class="form-input" min="0" value="0">
                        </div>
                        <div>
                            <label for="studentPrimaryFemale" class="block text-gray-700 text-sm font-bold mb-2">إناث ابتدائي:</label>
                            <input type="number" id="studentPrimaryFemale" class="form-input" min="0" value="0">
                        </div>
                        <div>
                            <label for="studentIntermediateMale" class="block text-gray-700 text-sm font-bold mb-2">ذكور متوسط:</label>
                            <input type="number" id="studentIntermediateMale" class="form-input" min="0" value="0">
                        </div>
                        <div>
                            <label for="studentIntermediateFemale" class="block text-gray-700 text-sm font-bold mb-2">إناث متوسط:</label>
                            <input type="number" id="studentIntermediateFemale" class="form-input" min="0" value="0">
                        </div>
                        <div>
                            <label for="studentSecondaryMale" class="block text-gray-700 text-sm font-bold mb-2">ذكور ثانوي:</label>
                            <input type="number" id="studentSecondaryMale" class="form-input" min="0" value="0">
                        </div>
                        <div>
                            <label for="studentSecondaryFemale" class="block text-gray-700 text-sm font-bold mb-2">إناث ثانوي:</label>
                            <input type="number" id="studentSecondaryFemale" class="form-input" min="0" value="0">
                        </div>
                        <div class="md:col-span-2">
                            <label for="schoolClassCount" class="block text-gray-700 text-sm font-bold mb-2">عدد الفصول:</label>
                            <input type="number" id="schoolClassCount" class="form-input" min="0" value="0">
                        </div>

                        <!-- New Fields for Schools -->
                        <div>
                            <label for="schoolAffiliation" class="block text-gray-700 text-sm font-bold mb-2">عائدية المدرسة:</label>
                            <input type="text" id="schoolAffiliation" class="form-input" placeholder="جهة عائدية المدرسة">
                        </div>
                        <div class="md:col-span-2">
                            <label for="schoolArchitecturalStatus" class="block text-gray-700 text-sm font-bold mb-2">حالتها العمرانية:</label>
                            <textarea id="schoolArchitecturalStatus" class="form-textarea" placeholder="وصف الحالة العمرانية للمدرسة"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="schoolObstacles" class="block text-gray-700 text-sm font-bold mb-2">العقبات:</label>
                            <textarea id="schoolObstacles" class="form-textarea" placeholder="العقبات التي تواجه المدرسة"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="schoolNeeds" class="block text-gray-700 text-sm font-bold mb-2">الاحتياجات:</label>
                            <textarea id="schoolNeeds" class="form-textarea" placeholder="احتياجات المدرسة"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="schoolProposedSolutions" class="block text-gray-700 text-sm font-bold mb-2">الحلول المقترفة:</label>
                            <textarea id="schoolProposedSolutions" class="form-textarea" placeholder="الحلول المقترحة للعقبات والاحتياجات"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة مدرسة</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">المدارس الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>الاسم</th>
                                <th>النوع</th>
                                <th>المحافظة</th>
                                <th>الموقع</th>
                                <th>الطلاب (ذ)</th>
                                <th>الطلاب (إ)</th>
                                <th>الفصول</th>
                                <th>العائدية</th>
                                <th>الحالة العمرانية</th>
                                <th>العقبات</th>
                                <th>الاحتياجات</th>
                                <th>الحلول المقترحة</th>
                            </tr>
                        </thead>
                        <tbody id="schoolsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Part 2: الشعبة الإدارية -->
        <div class="mb-8">
            <h2 class="text-3xl font-bold text-gray-700 mb-6 text-center border-b-2 border-blue-500 pb-2">الشعبة الإدارية</h2>

            <!-- Administrative Resources Section -->
            <div class="card">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">الموارد الإدارية</h3>
                <form id="addAdministrativeResourceForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="adminEmployeeName" class="block text-gray-700 text-sm font-bold mb-2">اسم الموظف:</label>
                            <input type="text" id="adminEmployeeName" class="form-input" placeholder="اسم الموظف" required>
                        </div>
                        <div>
                            <label for="adminPosition" class="block text-gray-700 text-sm font-bold mb-2">المنصب:</label>
                            <input type="text" id="adminPosition" class="form-input" placeholder="المنصب" required>
                        </div>
                        <div>
                            <label for="adminGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="adminGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div>
                            <label for="adminAppointmentDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ التعيين:</label>
                            <input type="date" id="adminAppointmentDate" class="form-input">
                        </div>
                        <div>
                            <label for="adminLeaveStatus" class="block text-gray-700 text-sm font-bold mb-2">حالة الإجازة:</label>
                            <select id="adminLeaveStatus" class="form-input">
                                <option value="غير مجاز">غير مجاز</option>
                                <option value="مجاز">مجاز</option>
                            </select>
                        </div>
                        <div>
                            <label for="adminLeaveType" class="block text-gray-700 text-sm font-bold mb-2">نوع الإجازة (إن وجدت):</label>
                            <input type="text" id="adminLeaveType" class="form-input" placeholder="مثال: إجازة طويلة، إجازة معين">
                        </div>
                        <!-- New fields for administrative resources -->
                        <div>
                            <label for="adminJobGrade" class="block text-gray-700 text-sm font-bold mb-2">الدرجة الوظيفية:</label>
                            <input type="text" id="adminJobGrade" class="form-input" placeholder="الدرجة الوظيفية">
                        </div>
                        <div>
                            <label for="adminJobCategory" class="block text-gray-700 text-sm font-bold mb-2">الفئة الوظيفية:</label>
                            <input type="text" id="adminJobCategory" class="form-input" placeholder="الفئة الوظيفية">
                        </div>
                        <div class="md:col-span-2">
                            <label for="adminDocumentsUpload" class="block text-gray-700 text-sm font-bold mb-2">المستمسكات (اسم الملف):</label>
                            <input type="text" id="adminDocumentsUpload" class="form-input" placeholder="اسم ملف المستمسك (مثال: هوية_أحمد.pdf)">
                        </div>
                        <div class="md:col-span-2">
                            <label for="adminNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="adminNotes" class="form-textarea" placeholder="ملاحظات حول الموظف أو حالته"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة موظف إداري</button>
                </form>
                <h4 class="text-xl font-semibold text-gray-700 mb-3">الموظفون الإداريون الحاليون:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>الاسم</th>
                                <th>المنصب</th>
                                <th>المحافظة</th>
                                <th>تاريخ التعيين</th>
                                <th>حالة الإجازة</th>
                                <th>نوع الإجازة</th>
                                <th>الدرجة</th>
                                <th>الفئة</th>
                                <th>المستمسكات</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="administrativeResourcesTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Citizen Affairs and Complaints Section (NEW) -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">شؤون المواطنين والشكاوى</h3>
                <form id="addCitizenComplaintForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="complaintNumber" class="block text-gray-700 text-sm font-bold mb-2">رقم الشكوى:</label>
                            <input type="text" id="complaintNumber" class="form-input" placeholder="رقم الشكوى" required>
                        </div>
                        <div>
                            <label for="complaintDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الشكوى:</label>
                            <input type="date" id="complaintDate" class="form-input" required>
                        </div>
                        <div>
                            <label for="complainantName" class="block text-gray-700 text-sm font-bold mb-2">اسم المشتكي:</label>
                            <input type="text" id="complainantName" class="form-input" placeholder="اسم المشتكي" required>
                        </div>
                        <div>
                            <label for="complaintGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="complaintGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label for="complaintSubject" class="block text-gray-700 text-sm font-bold mb-2">موضوع الشكوى:</label>
                            <textarea id="complaintSubject" class="form-textarea" placeholder="موضوع الشكوى" required></textarea>
                        </div>
                        <div>
                            <label for="complaintStatus" class="block text-gray-700 text-sm font-bold mb-2">حالة الشكوى:</label>
                            <select id="complaintStatus" class="form-input">
                                <option value="قيد المراجعة">قيد المراجعة</option>
                                <option value="تم الحل">تم الحل</option>
                                <option value="معلقة">معلقة</option>
                                <option value="تم الرفض">تم الرفض</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label for="complaintNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="complaintNotes" class="form-textarea" placeholder="ملاحظات إضافية حول الشكوى"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة شكوى</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">الشكاوى الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>رقم الشكوى</th>
                                <th>التاريخ</th>
                                <th>اسم المشتكي</th>
                                <th>المحافظة</th>
                                <th>الموضوع</th>
                                <th>الحالة</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="citizenComplaintsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Incoming Mail Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">البريد الوارد</h3>
                <form id="addIncomingMailForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="incomingMailLetterNumber" class="block text-gray-700 text-sm font-bold mb-2">رقم الكتاب:</label>
                            <input type="text" id="incomingMailLetterNumber" class="form-input" placeholder="رقم الكتاب الوارد" required>
                        </div>
                        <div>
                            <label for="incomingMailLetterDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الكتاب:</label>
                            <input type="date" id="incomingMailLetterDate" class="form-input" required>
                        </div>
                        <div>
                            <label for="incomingMailSender" class="block text-gray-700 text-sm font-bold mb-2">الجهة المرسلة:</label>
                            <input type="text" id="incomingMailSender" class="form-input" placeholder="اسم الجهة المرسلة" required>
                        </div>
                        <div>
                            <label for="incomingMailGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="incomingMailGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label for="incomingMailSubject" class="block text-gray-700 text-sm font-bold mb-2">الموضوع:</label>
                            <textarea id="incomingMailSubject" class="form-textarea" placeholder="موضوع الكتاب الوارد" required></textarea>
                        </div>
                        <div>
                            <label for="incomingMailFollowupStatus" class="block text-gray-700 text-sm font-bold mb-2">حالة المتابعة:</label>
                            <input type="text" id="incomingMailFollowupStatus" class="form-input" placeholder="حالة المتابعة">
                        </div>
                        <div class="md:col-span-2">
                            <label for="incomingMailNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="incomingMailNotes" class="form-textarea" placeholder="ملاحظات إضافية"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة كتاب وارد</button>
                </form>
                
                <div class="flex flex-col md:flex-row gap-4 mb-4">
                    <input type="text" id="incomingMailSearchQuery" class="form-input flex-grow md:w-auto" placeholder="بحث بالرقم، التاريخ، الموضوع، الجهة المرسلة...">
                    <button id="searchIncomingMailBtn" class="btn btn-secondary flex-shrink-0">بحث</button>
                </div>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">الكتب الواردة الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>رقم الكتاب</th>
                                <th>تاريخه</th>
                                <th>المرسل</th>
                                <th>المحافظة</th>
                                <th>الموضوع</th>
                                <th>حالة المتابعة</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="incomingMailTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Outgoing Mail Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">البريد الصادر</h3>
                <form id="addOutgoingMailForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="outgoingMailLetterNumber" class="block text-gray-700 text-sm font-bold mb-2">رقم الكتاب:</label>
                            <input type="text" id="outgoingMailLetterNumber" class="form-input" placeholder="رقم الكتاب الصادر" required>
                        </div>
                        <div>
                            <label for="outgoingMailLetterDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الكتاب:</label>
                            <input type="date" id="outgoingMailLetterDate" class="form-input" required>
                        </div>
                        <div>
                            <label for="outgoingMailRecipient" class="block text-gray-700 text-sm font-bold mb-2">الجهة الصادر إليها:</label>
                            <input type="text" id="outgoingMailRecipient" class="form-input" placeholder="اسم الجهة الصادر إليها" required>
                        </div>
                        <div>
                            <label for="outgoingMailGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="outgoingMailGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label for="outgoingMailSubject" class="block text-gray-700 text-sm font-bold mb-2">الموضوع:</label>
                            <textarea id="outgoingMailSubject" class="form-textarea" placeholder="موضوع الكتاب الصادر" required></textarea>
                        </div>
                        <div>
                            <label for="outgoingMailFollowupStatus" class="block text-gray-700 text-sm font-bold mb-2">حالة المتابعة:</label>
                            <input type="text" id="outgoingMailFollowupStatus" class="form-input" placeholder="حالة المتابعة">
                        </div>
                        <div class="md:col-span-2">
                            <label for="outgoingMailNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="outgoingMailNotes" class="form-textarea" placeholder="ملاحظات إضافية"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة كتاب صادر</button>
                </form>

                <div class="flex flex-col md:flex-row gap-4 mb-4">
                    <input type="text" id="outgoingMailSearchQuery" class="form-input flex-grow md:w-auto" placeholder="بحث بالرقم، التاريخ، الموضوع، الجهة الصادر إليها...">
                    <button id="searchOutgoingMailBtn" class="btn btn-secondary flex-shrink-0">بحث</button>
                </div>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">الكتب الصادرة الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>رقم الكتاب</th>
                                <th>تاريخه</th>
                                <th>الجهة الصادرة إليها</th>
                                <th>المحافظة</th>
                                <th>الموضوع</th>
                                <th>حالة المتابعة</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="outgoingMailTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Outgoing Circulars Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">التعميمات الصادرة</h3>
                <form id="addOutgoingCircularForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="outgoingCircularNumber" class="block text-gray-700 text-sm font-bold mb-2">رقم التعميم:</label>
                            <input type="text" id="outgoingCircularNumber" class="form-input" placeholder="رقم التعميم الصادر" required>
                        </div>
                        <div>
                            <label for="outgoingCircularDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ التعميم:</label>
                            <input type="date" id="outgoingCircularDate" class="form-input" required>
                        </div>
                        <div>
                            <label for="outgoingCircularRecipient" class="block text-gray-700 text-sm font-bold mb-2">الجهة الصادر إليها:</label>
                            <input type="text" id="outgoingCircularRecipient" class="form-input" placeholder="اسم الجهة الصادر إليها" required>
                        </div>
                        <div>
                            <label for="outgoingCircularGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="outgoingCircularGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label for="outgoingCircularSubject" class="block text-gray-700 text-sm font-bold mb-2">الموضوع:</label>
                            <textarea id="outgoingCircularSubject" class="form-textarea" placeholder="موضوع التعميم الصادر" required></textarea>
                        </div>
                        <div>
                            <label for="outgoingCircularFollowupStatus" class="block text-gray-700 text-sm font-bold mb-2">حالة المتابعة:</label>
                            <input type="text" id="outgoingCircularFollowupStatus" class="form-input" placeholder="حالة المتابعة">
                        </div>
                        <div class="md:col-span-2">
                            <label for="outgoingCircularNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="outgoingCircularNotes" class="form-textarea" placeholder="ملاحظات إضافية"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة تعميم صادر</button>
                </form>

                <div class="flex flex-col md:flex-row gap-4 mb-4">
                    <input type="text" id="outgoingCircularSearchQuery" class="form-input flex-grow md:w-auto" placeholder="بحث بالرقم، التاريخ، الموضوع، الجهة الصادرة إليها...">
                    <button id="searchOutgoingCircularsBtn" class="btn btn-secondary flex-shrink-0">بحث</button>
                </div>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">التعميمات الصادرة الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>رقم التعميم</th>
                                <th>تاريخه</th>
                                <th>الجهة الصادرة إليها</th>
                                <th>المحافظة</th>
                                <th>الموضوع</th>
                                <th>حالة المتابعة</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="outgoingCircularsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Part 3: التخطيط والفعاليات -->
        <div class="mb-8">
            <h2 class="text-3xl font-bold text-gray-700 mb-6 text-center border-b-2 border-blue-500 pb-2">التخطيط والفعاليات</h2>

            <!-- Activity Tracking Section -->
            <div class="card">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">تتبع الأنشطة والفعاليات</h3>
                <form id="addActivityForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="activityName" class="block text-gray-700 text-sm font-bold mb-2">اسم النشاط/الفعالية:</label>
                            <input type="text" id="activityName" class="form-input" placeholder="اسم النشاط" required>
                        </div>
                        <div>
                            <label for="activityDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ النشاط:</label>
                            <input type="date" id="activityDate" class="form-input" required>
                        </div>
                        <div>
                            <label for="activityType" class="block text-gray-700 text-sm font-bold mb-2">نوع النشاط:</label>
                            <input type="text" id="activityType" class="form-input" placeholder="مثال: دينية، ثقافية، توعية">
                        </div>
                        <div>
                            <label for="activityGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="activityGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label for="activityParticipants" class="block text-gray-700 text-sm font-bold mb-2">المشاركون/الجمهور المستهدف:</label>
                            <textarea id="activityParticipants" class="form-textarea" placeholder="وصف المشاركين أو الجمهور المستهدف"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="activityResources" class="block text-gray-700 text-sm font-bold mb-2">الموارد المستخدمة:</label>
                            <textarea id="activityResources" class="form-textarea" placeholder="الموارد البشرية، المادية، إلخ"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="activityResults" class="block text-gray-700 text-sm font-bold mb-2">النتائج/المخرجات:</label>
                            <textarea id="activityResults" class="form-textarea" placeholder="النتائج التي تحققت من النشاط"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="activityNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="activityNotes" class="form-textarea" placeholder="ملاحظات إضافية"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة نشاط/فعالية</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">الأنشطة والفعاليات الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>الاسم</th>
                                <th>التاريخ</th>
                                <th>النوع</th>
                                <th>المحافظة</th>
                                <th>المشاركون</th>
                                <th>الموارد</th>
                                <th>النتائج</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="activitiesTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Planning and Follow-up Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">التخطيط والمتابعة</h3>
                <form id="addPlanForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="planName" class="block text-gray-700 text-sm font-bold mb-2">اسم الخطة/المشروع:</label>
                            <input type="text" id="planName" class="form-input" placeholder="اسم الخطة" required>
                        </div>
                        <div>
                            <label for="planType" class="block text-gray-700 text-sm font-bold mb-2">نوع الخطة:</label>
                            <input type="text" id="planType" class="form-input" placeholder="مثال: استراتيجية، تشغيلية">
                        </div>
                        <div>
                            <label for="planGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="planGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div>
                            <label for="planStartDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ البدء:</label>
                            <input type="date" id="planStartDate" class="form-input">
                        </div>
                        <div>
                            <label for="planEndDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الانتهاء:</label>
                            <input type="date" id="planEndDate" class="form-input">
                        </div>
                        <div class="md:col-span-2">
                            <label for="planKPIs" class="block text-gray-700 text-sm font-bold mb-2">مؤشرات الأداء الرئيسية (KPIs):</label>
                            <textarea id="planKPIs" class="form-textarea" placeholder="وصف مؤشرات الأداء الرئيسية"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="planProgress" class="block text-gray-700 text-sm font-bold mb-2">التقدم/الحالة:</label>
                            <textarea id="planProgress" class="form-textarea" placeholder="وصف التقدم المحرز وحالة الخطة"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="planNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="planNotes" class="form-textarea" placeholder="ملاحظات إضافية حول الخطة"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة خطة/متابعة</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">الخطط الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>الاسم</th>
                                <th>النوع</th>
                                <th>المحافظة</th>
                                <th>تاريخ البدء</th>
                                <th>تاريخ الانتهاء</th>
                                <th>مؤشرات الأداء</th>
                                <th>التقدم</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="plansTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Part 4: إدارة الأصول والمشاريع -->
        <div class="mb-8">
            <h2 class="text-3xl font-bold text-gray-700 mb-6 text-center border-b-2 border-blue-500 pb-2">إدارة الأصول والمشاريع</h2>

            <!-- Endowed Properties and Investment Section -->
            <div class="card">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">الأملاك الموقوفة والاستثمار</h3>
                <form id="addEndowedPropertyForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="propertyName" class="block text-gray-700 text-sm font-bold mb-2">اسم العقار:</label>
                            <input type="text" id="propertyName" class="form-input" placeholder="اسم العقار أو وصفه" required>
                        </div>
                        <div>
                            <label for="propertyType" class="block text-gray-700 text-sm font-bold mb-2">نوع العقار:</label>
                            <select id="propertyType" class="form-input" required>
                                <option value="">اختر النوع</option>
                                <option value="أرض">أرض</option>
                                <option value="مبنى">مبنى</option>
                                <option value="مؤسسة دينية">مؤسسة دينية</option>
                                <option value="أخرى">أخرى</option>
                            </select>
                        </div>
                        <div>
                            <label for="propertyGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="propertyGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div>
                            <label for="propertyLocation" class="block text-gray-700 text-sm font-bold mb-2">الموقع (العنوان/المنطقة):</label>
                            <input type="text" id="propertyLocation" class="form-input" placeholder="العنوان أو المنطقة" required>
                        </div>
                        <div>
                            <label for="endowmentPropertyType" class="block text-gray-700 text-sm font-bold mb-2">نوع الوقف:</label>
                            <!-- Dropdown for Endowment Type -->
                            <select id="endowmentPropertyType" class="form-input">
                                <option value="">اختر نوع الوقف</option>
                                <option value="خيري">خيري</option>
                                <option value="ذري">ذري</option>
                                <option value="مضبوط">مضبوط</option>
                                <option value="غير ذلك">غير ذلك</option>
                            </select>
                        </div>
                        <div>
                            <label for="endowerName" class="block text-gray-700 text-sm font-bold mb-2">اسم الواقف:</label>
                            <input type="text" id="endowerName" class="form-input" placeholder="اسم الواقف (إذا توفر)">
                        </div>
                        <div>
                            <label for="propertyLegalStatus" class="block text-gray-700 text-sm font-bold mb-2">الحالة القانونية:</label>
                            <!-- Dropdown for Legal Status -->
                            <select id="propertyLegalStatus" class="form-input">
                                <option value="">اختر الحالة القانونية</option>
                                <option value="مسجل">مسجل</option>
                                <option value="قيد المراجعة">قيد المراجعة</option>
                                <option value="متنازع عليه">متنازع عليه</option>
                                <option value="مجهول العائدية">مجهول العائدية</option>
                            </select>
                        </div>
                        <div>
                            <label for="investmentStatus" class="block text-gray-700 text-sm font-bold mb-2">حالة الاستثمار:</label>
                            <select id="investmentStatus" class="form-input">
                                <option value="غير مستثمر">غير مستثمر</option>
                                <option value="مستثمر">مستثمر</option>
                                <option value="متاح للاستثمار">متاح للاستثمار</option>
                            </select>
                        </div>
                        <div>
                            <label for="investmentType" class="block text-gray-700 text-sm font-bold mb-2">نوع الاستثمار (إن وجد):</label>
                            <input type="text" id="investmentType" class="form-input" placeholder="مثال: إيجار، مساطحة، تطوير">
                        </div>
                        <div>
                            <label for="contractNumber" class="block text-gray-700 text-sm font-bold mb-2">رقم العقد (إن وجد):</label>
                            <input type="text" id="contractNumber" class="form-input" placeholder="رقم العقد">
                        </div>
                        <div>
                            <label for="contractStartDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ بدء العقد:</label>
                            <input type="date" id="contractStartDate" class="form-input">
                        </div>
                        <div>
                            <label for="contractEndDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الانتهاء:</label>
                            <input type="date" id="contractEndDate" class="form-input">
                        </div>
                        <div>
                            <label for="annualRevenue" class="block text-gray-700 text-sm font-bold mb-2">العائد السنوي المتوقع/الفعلي:</label>
                            <input type="number" id="annualRevenue" class="form-input" min="0" placeholder="بالدينار العراقي">
                        </div>
                        <div class="md:col-span-2">
                            <label for="propertyNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="propertyNotes" class="form-textarea" placeholder="ملاحظات إضافية حول العقار أو الاستثمار"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة عقار/استثمار</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">الأملاك الموقوفة والاستثمارات الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>اسم العقار</th>
                                <th>نوع العقار</th>
                                <th>المحافظة</th>
                                <th>الموقع</th>
                                <th>الواقف</th>
                                <th>حالة الاستثمار</th>
                                <th>نوع الاستثمار</th>
                                <th>رقم العقد</th>
                                <th>العائد السنوي</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="endowedPropertiesTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Engineering Projects Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">المشاريع الهندسية</h3>
                <form id="addEngineeringProjectForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="projectName" class="block text-gray-700 text-sm font-bold mb-2">اسم المشروع:</label>
                            <input type="text" id="projectName" class="form-input" placeholder="اسم المشروع الهندسي" required>
                        </div>
                        <div>
                            <label for="projectType" class="block text-gray-700 text-sm font-bold mb-2">نوع المشروع:</label>
                            <select id="projectType" class="form-input" required>
                                <option value="">اختر النوع</option>
                                <option value="إنشاء">إنشاء</option>
                                <option value="ترميم">ترميم</option>
                                <option value="صيانة">صيانة</option>
                                <option value="تطوير">تطوير</option>
                                <option value="أخرى">أخرى</option>
                            </select>
                        </div>
                        <div>
                            <label for="projectGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="projectGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div>
                            <label for="projectLocation" class="block text-gray-700 text-sm font-bold mb-2">الموقع:</label>
                            <input type="text" id="projectLocation" class="form-input" placeholder="موقع المشروع" required>
                        </div>
                        <div>
                            <label for="projectStatus" class="block text-gray-700 text-sm font-bold mb-2">الحالة:</label>
                            <select id="projectStatus" class="form-input">
                                <option value="قيد التخطيط">قيد التخطيط</option>
                                <option value="قيد التنفيذ">قيد التنفيذ</option>
                                <option value="مكتمل">مكتمل</option>
                                <option value="متوقف">متوقف</option>
                                <option value="متأخر">متأخر</option>
                            </select>
                        </div>
                        <div>
                            <label for="projectBudget" class="block text-gray-700 text-sm font-bold mb-2">الميزانية الأصلية (بالدينار العراقي):</label>
                            <input type="number" id="projectBudget" class="form-input" min="0" value="0" placeholder="الميزانية بالدينار العراقي">
                        </div>
                        <div>
                            <label for="projectStartDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ البدء:</label>
                            <input type="date" id="projectStartDate" class="form-input">
                        </div>
                        <div>
                            <label for="projectEndDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الانتهاء الأصلي (المتوقع/الفعلي):</label>
                            <input type="date" id="projectEndDate" class="form-input">
                        </div>
                        <div>
                            <label for="projectContractor" class="block text-gray-700 text-sm font-bold mb-2">المقاول:</label>
                            <input type="text" id="projectContractor" class="form-input" placeholder="اسم المقاول">
                        </div>
                        <div>
                            <label for="supervisingEngineer" class="block text-gray-700 text-sm font-bold mb-2">المهندس المشرف:</label>
                            <input type="text" id="supervisingEngineer" class="form-input" placeholder="اسم المهندس المشرف">
                        </div>
                        <div class="md:col-span-2">
                            <label for="projectDocuments" class="block text-gray-700 text-sm font-bold mb-2">المستندات الهندسية (اسم الملف):</label>
                            <input type="text" id="projectDocuments" class="form-input" placeholder="اسم ملف المخططات/الوثائق (مثال: مخطط_مشروع1.pdf)">
                        </div>
                        <div>
                            <label for="progressPercentage" class="block text-gray-700 text-sm font-bold mb-2">نسبة التقدم (%):</label>
                            <input type="number" id="progressPercentage" class="form-input" min="0" max="100" value="0">
                        </div>
                        
                        <div class="md:col-span-2">
                            <label for="extendedPeriodsDays" class="block text-gray-700 text-sm font-bold mb-2">المدد الإضافية العامة (بالأيام):</label>
                            <input type="number" id="extendedPeriodsDays" class="form-input" min="0" value="0" placeholder="عدد الأيام الإضافية">
                        </div>

                        <!-- Consolidated Change Orders -->
                        <div class="md:col-span-2 border-t pt-4 mt-4 border-gray-200">
                            <h4 class="text-lg font-semibold text-gray-700 mb-2">أوامر الغيار (المجموع الكلي)</h4>
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                <div>
                                    <label for="totalChangeOrdersDuration" class="block text-gray-700 text-sm font-bold mb-2">مجموع المدة (أيام):</label>
                                    <input type="number" id="totalChangeOrdersDuration" class="form-input" min="0" value="0" placeholder="إجمالي مدة أوامر الغيار">
                                </div>
                                <div>
                                    <label for="totalChangeOrdersAmount" class="block text-gray-700 text-sm font-bold mb-2">مجموع المبلغ (د.ع):</label>
                                    <input type="number" id="totalChangeOrdersAmount" class="form-input" min="0" value="0" placeholder="إجمالي مبلغ أوامر الغيار">
                                </div>
                            </div>
                        </div>

                        <!-- Granted Advances -->
                        <div>
                            <label for="grantedAdvancesCount" class="block text-gray-700 text-sm font-bold mb-2">عدد السلف الممنوحة:</label>
                            <input type="number" id="grantedAdvancesCount" class="form-input" min="0" value="0" placeholder="عدد السلف الممنوحة">
                        </div>
                        <div>
                            <label for="grantedAdvancesAmount" class="block text-gray-700 text-sm font-bold mb-2">مبلغ السلف الممنوحة (د.ع):</label>
                            <input type="number" id="grantedAdvancesAmount" class="form-input" min="0" value="0" placeholder="مبلغ السلف الممنوحة">
                        </div>

                        <!-- Operational Advances -->
                        <div>
                            <label for="operationalAdvancesCount" class="block text-gray-700 text-sm font-bold mb-2">عدد السلف التشغيلية:</label>
                            <input type="number" id="operationalAdvancesCount" class="form-input" min="0" value="0" placeholder="عدد السلف التشغيلية">
                        </div>
                        <div>
                            <label for="operationalAdvancesAmount" class="block text-gray-700 text-sm font-bold mb-2">مبلغ السلف التشغيلية (د.ع):</label>
                            <input type="number" id="operationalAdvancesAmount" class="form-input" min="0" value="0" placeholder="مبلغ السلف التشغيلية">
                        </div>

                        <!-- New Field: Delay Fines and Reasons -->
                        <div class="md:col-span-2">
                            <label for="delayFinesAndReasons" class="block text-gray-700 text-sm font-bold mb-2">الغرامات التأخيرية وأسبابها:</label>
                            <textarea id="delayFinesAndReasons" class="form-textarea" placeholder="الغرامات التأخيرية وأسبابها"></textarea>
                        </div>

                        <div class="md:col-span-2">
                            <label for="projectObstacles" class="block text-gray-700 text-sm font-bold mb-2">العقبات:</label>
                            <textarea id="projectObstacles" class="form-textarea" placeholder="العقبات التي تواجه المشروع"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="projectSolutions" class="block text-gray-700 text-sm font-bold mb-2">الحلول المقترحة:</label>
                            <textarea id="projectSolutions" class="form-textarea" placeholder="الحلول المقترحة للعقبات"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="projectNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="projectNotes" class="form-textarea" placeholder="ملاحظات إضافية حول المشروع"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة مشروع هندسي</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">المشاريع الهندسية الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>اسم المشروع</th>
                                <th>النوع</th>
                                <th>المحافظة</th>
                                <th>الموقع</th>
                                <th>الحالة</th>
                                <th>الميزانية الأصلية</th>
                                <th>الميزانية الكلية (د.ع)</th>
                                <th>تاريخ البدء</th>
                                <th>تاريخ الانتهاء الأصلي</th>
                                <th>المدة الكلية (أيام)</th>
                                <th>المقاول</th>
                                <th>المهندس المشرف</th>
                                <th>المستندات</th>
                                <th>التقدم (%)</th>
                                <th>مدد إضافية عامة (أيام)</th>
                                <th>مجموع أوامر الغيار (مدة)</th>
                                <th>مجموع أوامر الغيار (مبلغ)</th>
                                <th>عدد سلف ممنوحة</th>
                                <th>مبلغ سلف ممنوحة</th>
                                <th>عدد سلف تشغيلية</th>
                                <th>مبلغ سلف تشغيلية</th>
                                <th>الغرامات التأخيرية وأسبابها</th>
                                <th>العقبات</th>
                                <th>الحلول</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="engineeringProjectsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Part 5: الجوانب القانونية والأمنية وتكنولوجيا المعلومات -->
        <div class="mb-8">
            <h2 class="text-3xl font-bold text-gray-700 mb-6 text-center border-b-2 border-blue-500 pb-2">الجوانب القانونية والأمنية وتكنولوجيا المعلومات</h2>

            <!-- Legal Affairs Section -->
            <div class="card">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">الشؤون القانونية</h3>
                <form id="addLegalAffairForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="legalCaseContractName" class="block text-gray-700 text-sm font-bold mb-2">اسم القضية/العقد:</label>
                            <input type="text" id="legalCaseContractName" class="form-input" placeholder="اسم القضية أو العقد" required>
                        </div>
                        <div>
                            <label for="legalAffairType" class="block text-gray-700 text-sm font-bold mb-2">النوع:</label>
                            <select id="legalAffairType" class="form-input" required>
                                <option value="">اختر النوع</option>
                                <option value="قضية">قضية</option>
                                <option value="عقد">عقد</option>
                                <option value="استشارة قانونية">استشارة قانونية</option>
                                <option value="أخرى">أخرى</option>
                            </select>
                        </div>
                        <div>
                            <label for="legalAffairGov" class="block text-gray-700 text-sm font-bold mb-2">المحافظة:</label>
                            <select id="legalAffairGov" class="form-input" required>
                                <option value="">اختر المحافظة</option>
                                <option value="البصرة">البصرة</option>
                                <option value="ميسان">ميسان</option>
                                <option value="ذي قار">ذي قار</option>
                            </select>
                        </div>
                        <div>
                            <label for="legalAffairStartDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ البدء:</label>
                            <input type="date" id="legalAffairStartDate" class="form-input">
                        </div>
                        <div>
                            <label for="legalAffairEndDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الانتهاء/الإغلاق:</label>
                            <input type="date" id="legalAffairEndDate" class="form-input">
                        </div>
                        <div>
                            <label for="legalAffairInvolvedParty" class="block text-gray-700 text-sm font-bold mb-2">الطرف المعني:</label>
                            <input type="text" id="legalAffairInvolvedParty" class="form-input" placeholder="اسم الطرف المعني">
                        </div>
                        <div>
                            <label for="legalAffairStatus" class="block text-gray-700 text-sm font-bold mb-2">الحالة:</label>
                            <select id="legalAffairStatus" class="form-input">
                                <option value="مفتوحة">مفتوحة</option>
                                <option value="مغلقة">مغلقة</option>
                                <option value="قيد المراجعة">قيد المراجعة</option>
                                <option value="معلقة">معلقة</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label for="legalAffairDocuments" class="block text-gray-700 text-sm font-bold mb-2">المستندات القانونية (اسم الملف):</label>
                            <input type="text" id="legalAffairDocuments" class="form-input" placeholder="اسم ملف المستندات (مثال: عقد_مقاول.pdf)">
                        </div>
                        <div class="md:col-span-2">
                            <label for="legalAffairNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="legalAffairNotes" class="form-textarea" placeholder="ملاحظات إضافية حول القضية أو العقد"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة شأن قانوني</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">الشؤون القانونية الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>اسم القضية/العقد</th>
                                <th>النوع</th>
                                <th>المحافظة</th>
                                <th>تاريخ البدء</th>
                                <th>تاريخ الانتهاء</th>
                                <th>الطرف المعني</th>
                                <th>الحالة</th>
                                <th>المستندات</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="legalAffairsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Security Clearances Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">التصاريح الأمنية</h3>
                <form id="addSecurityClearanceForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="clearanceNumber" class="block text-gray-700 text-sm font-bold mb-2">رقم التصريح:</label>
                            <input type="text" id="clearanceNumber" class="form-input" placeholder="رقم التصريح الأمني" required>
                        </div>
                        <div>
                            <label for="clearanceType" class="block text-gray-700 text-sm font-bold mb-2">نوع التصريح:</label>
                            <input type="text" id="clearanceType" class="form-input" placeholder="مثال: دخول، وصول">
                        </div>
                        <div>
                            <label for="clearanceIssueDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الإصدار:</label>
                            <input type="date" id="clearanceIssueDate" class="form-input">
                        </div>
                        <div>
                            <label for="clearanceExpiryDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الانتهاء:</label>
                            <input type="date" id="clearanceExpiryDate" class="form-input">
                        </div>
                        <div>
                            <label for="clearanceHolderName" class="block text-gray-700 text-sm font-bold mb-2">اسم حامل التصريح:</label>
                            <input type="text" id="clearanceHolderName" class="form-input" placeholder="اسم حامل التصريح" required>
                        </div>
                        <div>
                            <label for="clearanceAccessLevel" class="block text-gray-700 text-sm font-bold mb-2">مستوى الوصول:</label>
                            <input type="text" id="clearanceAccessLevel" class="form-input" placeholder="مثال: محدود، كامل">
                        </div>
                        <div class="md:col-span-2">
                            <label for="clearanceNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="clearanceNotes" class="form-textarea" placeholder="ملاحظات إضافية حول التصريح"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة تصريح أمني</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">التصاريح الأمنية الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>رقم التصريح</th>
                                <th>النوع</th>
                                <th>تاريخ الإصدار</th>
                                <th>تاريخ الانتهاء</th>
                                <th>اسم الحامل</th>
                                <th>مستوى الوصول</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="securityClearancesTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Information Technology Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">تكنولوجيا المعلومات</h3>
                <form id="addITAssetForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="itAssetName" class="block text-gray-700 text-sm font-bold mb-2">اسم الأصل:</label>
                            <input type="text" id="itAssetName" class="form-input" placeholder="اسم الجهاز أو البرنامج" required>
                        </div>
                        <div>
                            <label for="itAssetType" class="block text-gray-700 text-sm font-bold mb-2">النوع:</label>
                            <select id="itAssetType" class="form-input" required>
                                <option value="">اختر النوع</option>
                                <option value="كمبيوتر">كمبيوتر</option>
                                <option value="طابعة">طابعة</option>
                                <option value="برنامج">برنامج</option>
                                <option value="خادم">خادم</option>
                                <option value="شبكة">شبكة</option>
                                <option value="أخرى">أخرى</option>
                            </select>
                        </div>
                        <div>
                            <label for="itAssetSerialNumber" class="block text-gray-700 text-sm font-bold mb-2">الرقم التسلسلي/الترخيص:</label>
                            <input type="text" id="itAssetSerialNumber" class="form-input" placeholder="الرقم التسلسلي أو مفتاح الترخيص">
                        </div>
                        <div>
                            <label for="itAssetAcquisitionDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ الاقتناء:</label>
                            <input type="date" id="itAssetAcquisitionDate" class="form-input">
                        </div>
                        <div>
                            <label for="itAssetStatus" class="block text-gray-700 text-sm font-bold mb-2">الحالة:</label>
                            <select id="itAssetStatus" class="form-input">
                                <option value="فعال">فعال</option>
                                <option value="معطل">معطل</option>
                                <option value="تحت الصيانة">تحت الصيانة</option>
                                <option value="مخزن">مخزن</option>
                            </select>
                        </div>
                        <div>
                            <label for="itAssetLocation" class="block text-gray-700 text-sm font-bold mb-2">الموقع/القسم:</label>
                            <input type="text" id="itAssetLocation" class="form-input" placeholder="موقع الأصل (مثال: مكتب، مخزن، قسم)">
                        </div>
                        <div class="md:col-span-2">
                            <label for="itAssetNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="itAssetNotes" class="form-textarea" placeholder="ملاحظات إضافية حول الأصل أو حالته"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة أصل تقني</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">أصول تكنولوجيا المعلومات الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>اسم الأصل</th>
                                <th>النوع</th>
                                <th>الرقم التسلسلي/الترخيص</th>
                                <th>تاريخ الاقتناء</th>
                                <th>الحالة</th>
                                <th>الموقع/القسم</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="itAssetsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Part 6: البحوث والتدقيق -->
        <div class="mb-8">
            <h2 class="text-3xl font-bold text-gray-700 mb-6 text-center border-b-2 border-blue-500 pb-2">البحوث والتدقيق</h2>

            <!-- Research and Studies Section -->
            <div class="card">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">وحدة البحوث والدراسات</h3>
                <form id="addResearchStudyForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="researchTitle" class="block text-gray-700 text-sm font-bold mb-2">عنوان البحث/الدراسة:</label>
                            <input type="text" id="researchTitle" class="form-input" placeholder="عنوان البحث" required>
                        </div>
                        <div>
                            <label for="researchAuthor" class="block text-gray-700 text-sm font-bold mb-2">المؤلف/الباحث:</label>
                            <input type="text" id="researchAuthor" class="form-input" placeholder="اسم المؤلف أو الباحث">
                        </div>
                        <div>
                            <label for="researchPublicationDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ النشر:</label>
                            <input type="date" id="researchPublicationDate" class="form-input">
                        </div>
                        <div class="md:col-span-2">
                            <label for="researchSummary" class="block text-gray-700 text-sm font-bold mb-2">الملخص:</label>
                            <textarea id="researchSummary" class="form-textarea" placeholder="ملخص للبحث أو الدراسة"></textarea>
                        </div>
                        <div>
                            <label for="libraryName" class="block text-gray-700 text-sm font-bold mb-2">اسم المكتبة (إن وجد):</label>
                            <input type="text" id="libraryName" class="form-input" placeholder="اسم المكتبة المركزية">
                        </div>
                        <div>
                            <label for="libraryLength" class="block text-gray-700 text-sm font-bold mb-2">طول المكتبة (متر):</label>
                            <input type="number" id="libraryLength" class="form-input" min="0" value="0" step="0.1">
                        </div>
                        <div>
                            <label for="libraryWidth" class="block text-gray-700 text-sm font-bold mb-2">عرض المكتبة (متر):</label>
                            <input type="number" id="libraryWidth" class="form-input" min="0" value="0" step="0.1">
                        </div>
                        <div>
                            <label for="libraryHeight" class="block text-gray-700 text-sm font-bold mb-2">ارتفاع المكتبة (متر):</label>
                            <input type="number" id="libraryHeight" class="form-input" min="0" value="0" step="0.1">
                        </div>
                        <div>
                            <label for="numBooks" class="block text-gray-700 text-sm font-bold mb-2">عدد الكتب:</label>
                            <input type="number" id="numBooks" class="form-input" min="0" value="0">
                        </div>
                        <div>
                            <label for="numReferences" class="block text-gray-700 text-sm font-bold mb-2">عدد المراجع:</label>
                            <input type="number" id="numReferences" class="form-input" min="0" value="0">
                        </div>
                        <div class="md:col-span-2">
                            <label for="researchNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="researchNotes" class="form-textarea" placeholder="ملاحظات إضافية حول البحث أو المكتبة"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة بحث/دراسة</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">البحوث والدراسات الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>العنوان</th>
                                <th>المؤلف</th>
                                <th>تاريخ النشر</th>
                                <th>الملخص</th>
                                <th>المكتبة</th>
                                <th>أبعادها (طxعxا)</th>
                                <th>عدد الكتب</th>
                                <th>عدد المراجع</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="researchStudiesTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Auditing and Oversight Section -->
            <div class="card mt-6">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">شعبة التدقيق والرقابة</h3>
                <form id="addAuditingReportForm" class="mb-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label for="auditingReportNumber" class="block text-gray-700 text-sm font-bold mb-2">رقم التقرير:</label>
                            <input type="text" id="auditingReportNumber" class="form-input" placeholder="رقم تقرير التدقيق" required>
                        </div>
                        <div>
                            <label for="auditingReportDate" class="block text-gray-700 text-sm font-bold mb-2">تاريخ التقرير:</label>
                            <input type="date" id="auditingReportDate" class="form-input" required>
                        </div>
                        <div>
                            <label for="auditingEntity" class="block text-gray-700 text-sm font-bold mb-2">الجهة المدققة:</label>
                            <input type="text" id="auditingEntity" class="form-input" placeholder="مثال: ديوان الرقابة المالية، داخلي" required>
                        </div>
                        <div class="md:col-span-2">
                            <label for="auditingObservations" class="block text-gray-700 text-sm font-bold mb-2">الملاحظات الواردة:</label>
                            <textarea id="auditingObservations" class="form-textarea" placeholder="الملاحظات والتجاوزات المكتشفة"></textarea>
                        </div>
                        <div class="md:col-span-2">
                            <label for="auditingRecommendations" class="block text-gray-700 text-sm font-bold mb-2">التوصيات:</label>
                            <textarea id="auditingRecommendations" class="form-textarea" placeholder="التوصيات المقدمة"></textarea>
                        </div>
                        <div>
                            <label for="auditingFollowupStatus" class="block text-gray-700 text-sm font-bold mb-2">حالة المتابعة:</label>
                            <input type="text" id="auditingFollowupStatus" class="form-input" placeholder="حالة متابعة التوصيات (مثال: تمت الإجابة، قيد المتابعة)">
                        </div>
                        <div>
                            <label for="auditedTransactionsCount" class="block text-gray-700 text-sm font-bold mb-2">عدد المعاملات المدققة:</label>
                            <input type="number" id="auditedTransactionsCount" class="form-input" min="0" value="0">
                        </div>
                        <div class="md:col-span-2">
                            <label for="auditingNotes" class="block text-gray-700 text-sm font-bold mb-2">ملاحظات:</label>
                            <textarea id="auditingNotes" class="form-textarea" placeholder="ملاحظات إضافية حول تقرير التدقيق"></textarea>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary mt-4">إضافة تقرير تدقيق</button>
                </form>

                <h4 class="text-xl font-semibold text-gray-700 mb-3">تقارير التدقيق الحالية:</h4>
                <div class="overflow-x-auto rounded-lg shadow">
                    <table class="table-auto">
                        <thead>
                            <tr>
                                <th>رقم التقرير</th>
                                <th>تاريخه</th>
                                <th>الجهة المدققة</th>
                                <th>الملاحظات</th>
                                <th>التوصيات</th>
                                <th>حالة المتابعة</th>
                                <th>عدد المعاملات المدققة</th>
                                <th>ملاحظات</th>
                            </tr>
                        </thead>
                        <tbody id="auditingReportsTableBody">
                            <!-- Data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Part 7: التقارير والملخصات -->
        <div class="mb-8">
            <h2 class="text-3xl font-bold text-gray-700 mb-6 text-center border-b-2 border-blue-500 pb-2">التقارير والملخصات</h2>

            <!-- Reports Section -->
            <div class="card">
                <h3 class="text-2xl font-semibold text-gray-700 mb-4">التقارير</h3>
                <button id="generateReportBtn" class="btn btn-secondary flex items-center justify-center">
                    <span id="reportSpinner" class="spinner hidden"></span>
                    توليد تقارير شاملة للمديريات
                </button>
                <div id="reportsContainer" class="mt-4">
                    <div id="basraReportOutput" class="mt-4 p-4 bg-gray-50 rounded-md border border-gray-200 text-gray-800 whitespace-pre-wrap">
                        <h4 class="text-xl font-semibold text-gray-700 mb-3">تقرير مديرية البصرة:</h4>
                        التقرير سيظهر هنا...
                    </div>
                    <div id="maysanReportOutput" class="mt-6 p-4 bg-gray-50 rounded-md border border-gray-200 text-gray-800 whitespace-pre-wrap">
                        <h4 class="text-xl font-semibold text-gray-700 mb-3">تقرير مديرية ميسان:</h4>
                        التقرير سيظهر هنا...
                    </div>
                    <div id="dhiQarReportOutput" class="mt-6 p-4 bg-gray-50 rounded-md border border-gray-200 text-gray-800 whitespace-pre-wrap">
                        <h4 class="text-xl font-semibold text-gray-700 mb-3">تقرير مديرية ذي قار:</h4>
                        التقرير سيظهر هنا...
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Designer Credit -->
    <div class="card text-center text-gray-600 mt-8">
        <p class="text-lg font-semibold mb-2">تصميم وإعداد البرنامج:</p>
        <p class="text-xl font-bold text-blue-700">رئيس مهندسين: رائد ابراهيم خليل ابراهيم</p>
    </div>
</div>

<!-- Firebase SDKs -->
<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
    import { getAuth, signInAnonymously, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";
    import { getFirestore, collection, addDoc, onSnapshot, query, serverTimestamp, getDocs } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";

    // Global variables provided by the Canvas environment
    const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
    const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
    // Initialize Firebase
    let app;
    let db;
    let auth;
    let userId = null; // Will be set after auth
    let isAuthReady = false;
    let isAuthenticated = false; // Track actual authentication status

    // DOM elements
    const userIdSpan = document.getElementById('user-id');
    const authStatusSpan = document.getElementById('auth-status');
    const authButton = document.getElementById('auth-button');
    const mainContentDiv = document.getElementById('main-content');

    // Store the full data arrays for client-side filtering
    let allIncomingMailData = [];
    let allOutgoingMailData = [];
    let allOutgoingCircularsData = [];
    let allActivitiesData = [];
    let allPlansData = [];
    let allEndowedPropertiesData = [];
    let allEngineeringProjectsData = [];
    let allLegalAffairsData = [];
    let allSecurityClearancesData = [];
    let allITAssetsData = [];
    let allResearchStudiesData = [];
    let allAuditingReportsData = [];
    let allCitizenComplaintsData = [];
    let allInstitutionsData = [];
    let allSchoolsData = [];
    let allAdministrativeResourcesData = [];


    // Function to show transient messages
    function showMessage(message, type = 'success') {
        const messageBox = document.getElementById('messageBox');
        messageBox.textContent = message;
        messageBox.className = 'message-box'; // Reset classes
        if (type === 'error') {
            messageBox.classList.add('error');
        }
        messageBox.style.display = 'block';
        messageBox.style.opacity = '1';
        setTimeout(() => {
            messageBox.style.opacity = '0';
            setTimeout(() => {
                messageBox.style.display = 'none';
            }, 500);
        }, 3000);
    }

    // Function to fetch data from Gemini API
    async function generateTextWithGemini(prompt) {
        const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=`; // Key handled by Canvas
        let chatHistory = [];
        chatHistory.push({ role: "user", parts: [{ text: prompt }] });
        const payload = { contents: chatHistory };

        try {
            const response = await fetch(apiUrl, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            });
            // Check for non-OK HTTP status
            if (!response.ok) {
                const errorText = await response.text();
                throw new Error(`HTTP error! status: ${response.status}, details: ${errorText}`);
            }
            const result = await response.json();

            if (result.candidates && result.candidates.length > 0 &&
                result.candidates[0].content && result.candidates[0].content.parts &&
                result.candidates[0].content.parts.length > 0) {
                return result.candidates[0].content.parts[0].text;
            } else {
                console.error("Gemini API returned an unexpected structure:", JSON.stringify(result, null, 2));
                throw new Error("Failed to generate text: Unexpected API response structure or missing content.");
            }
        } catch (error) {
            console.error("Error calling Gemini API:", error);
            // Propagate the specific error message
            throw new Error(`حدث خطأ أثناء توليد التقرير من Gemini AI: ${error.message}`);
        }
    }


    // Initialize Firebase and set up authentication listener
    window.onload = async () => {
        try {
            app = initializeApp(firebaseConfig);
            db = getFirestore(app);
            auth = getAuth(app);

            onAuthStateChanged(auth, async (user) => {
                if (user) {
                    userId = user.uid;
                    isAuthenticated = true;
                    userIdSpan.textContent = userId;
                    authStatusSpan.textContent = 'مسجل الدخول';
                    authButton.textContent = 'تسجيل الخروج';
                    mainContentDiv.classList.remove('hidden'); // Show content on login
                    showMessage('تم تسجيل الدخول بنجاح!', 'success');
                } else {
                    userId = null;
                    isAuthenticated = false;
                    userIdSpan.textContent = 'غير مسجل الدخول';
                    authStatusSpan.textContent = 'غير مسجل الدخول';
                    authButton.textContent = 'تسجيل الدخول / البدء';
                    mainContentDiv.classList.add('hidden'); // Hide content on logout
                }
                isAuthReady = true; // Mark auth as ready regardless of success or failure for data loading
            });

        } catch (e) {
            console.error("Error initializing Firebase:", e);
            showMessage("خطأ في تهيئة Firebase.", 'error');
        }
    };

    // Handle authentication button click
    authButton.addEventListener('click', async () => {
        if (isAuthenticated) {
            // Log out
            try {
                await signOut(auth);
                showMessage('تم تسجيل الخروج بنجاح!', 'success');
            } catch (error) {
                console.error("Error signing out:", error);
                showMessage('فشل تسجيل الخروج.', 'error');
            }
        } else {
            // Try to sign in (anonymously or with signInWithEmailAndPassword if available)
             {
                try {
                    await signInWithEmailAndPassword(auth;
                } catch (error) {
                    console.error("Error signing in with signInWithEmailAndPassword:", error);
                    try {
                        await signInAnonymously(auth);
                    } catch (anonError) {
                        console.error("Error signing in anonymously:", anonError);
                        showMessage('فشل تسجيل الدخول. يرجى تحديث الصفحة.', 'error');
                    }
                }
            } else {
                try {
                    await signInAnonymously(auth);
                } catch (anonError) {
                    console.error("Error signing in anonymously:", anonError);
                    showMessage('فشل تسجيل الدخول. يرجى تحديث الصفحة.', 'error');
                }
            }
        }
    });


    // Unsubscribe functions for all listeners
    let unsubscribeInstitutions;
    let unsubscribeSchools;
    let unsubscribeAdministrativeResources;
    let unsubscribeIncomingMail;
    let unsubscribeOutgoingMail;
    let unsubscribeOutgoingCirculars;
    let unsubscribeActivities;
    let unsubscribePlans;
    let unsubscribeEndowedProperties;
    let unsubscribeEngineeringProjects;
    let unsubscribeLegalAffairs;
    let unsubscribeSecurityClearances;
    let unsubscribeITAssets;
    let unsubscribeResearchStudies;
    let unsubscribeAuditingReports;
    let unsubscribeCitizenComplaints;


    const setupFirestoreListeners = () => {
        if (!db || !userId || !isAuthReady || !isAuthenticated) {
            // If auth is not ready or userId is not set, or not authenticated, postpone listeners setup
            console.log("Firestore listeners postponed: Auth not ready, userId not set, or not authenticated.");
            return;
        }

        // Unsubscribe from previous listeners if they exist to avoid duplicates
        if (unsubscribeInstitutions) unsubscribeInstitutions();
        if (unsubscribeSchools) unsubscribeSchools();
        if (unsubscribeAdministrativeResources) unsubscribeAdministrativeResources();
        if (unsubscribeIncomingMail) unsubscribeIncomingMail();
        if (unsubscribeOutgoingMail) unsubscribeOutgoingMail();
        if (unsubscribeOutgoingCirculars) unsubscribeOutgoingCirculars();
        if (unsubscribeActivities) unsubscribeActivities();
        if (unsubscribePlans) unsubscribePlans();
        if (unsubscribeEndowedProperties) unsubscribeEndowedProperties();
        if (unsubscribeEngineeringProjects) unsubscribeEngineeringProjects();
        if (unsubscribeLegalAffairs) unsubscribeLegalAffairs();
        if (unsubscribeSecurityClearances) unsubscribeSecurityClearances();
        if (unsubscribeITAssets) unsubscribeITAssets();
        if (unsubscribeResearchStudies) unsubscribeResearchStudies();
        if (unsubscribeAuditingReports) unsubscribeAuditingReports();
        if (unsubscribeCitizenComplaints) unsubscribeCitizenComplaints();


        // Institutions Listener
        const institutionsColRef = collection(db, `artifacts/${appId}/users/${userId}/institutions`);
        const qInstitutions = query(institutionsColRef);
        unsubscribeInstitutions = onSnapshot(qInstitutions, (snapshot) => {
            allInstitutionsData = [];
            snapshot.forEach(doc => {
                allInstitutionsData.push({ id: doc.id, ...doc.data() });
            });
            displayInstitutions(allInstitutionsData);
        }, (error) => {
            console.error("Error fetching institutions (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات المؤسسات.", 'error');
        });

        // Schools Listener
        const schoolsColRef = collection(db, `artifacts/${appId}/users/${userId}/schools`);
        const qSchools = query(schoolsColRef);
        unsubscribeSchools = onSnapshot(qSchools, (snapshot) => {
            allSchoolsData = [];
            snapshot.forEach(doc => {
                allSchoolsData.push({ id: doc.id, ...doc.data() });
            });
            displaySchools(allSchoolsData);
        }, (error) => {
            console.error("Error fetching schools (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات المدارس.", 'error');
        });

        // Administrative Resources Listener
        const adminResourcesColRef = collection(db, `artifacts/${appId}/users/${userId}/administrativeResources`);
        const qAdminResources = query(adminResourcesColRef);
        unsubscribeAdministrativeResources = onSnapshot(qAdminResources, (snapshot) => {
            allAdministrativeResourcesData = [];
            snapshot.forEach(doc => {
                allAdministrativeResourcesData.push({ id: doc.id, ...doc.data() });
            });
            displayAdministrativeResources(allAdministrativeResourcesData);
        }, (error) => {
            console.error("Error fetching administrative resources (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات الموارد الإدارية.", 'error');
        });

        // Citizen Complaints Listener
        const citizenComplaintsColRef = collection(db, `artifacts/${appId}/users/${userId}/citizenComplaints`);
        const qCitizenComplaints = query(citizenComplaintsColRef);
        unsubscribeCitizenComplaints = onSnapshot(qCitizenComplaints, (snapshot) => {
            allCitizenComplaintsData = []; // Store for filtering
            snapshot.forEach(doc => {
                allCitizenComplaintsData.push({ id: doc.id, ...doc.data() });
            });
            displayCitizenComplaints(allCitizenComplaintsData);
        }, (error) => {
            console.error("Error fetching citizen complaints (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات شكاوى المواطنين.", 'error');
        });

        // Incoming Mail Listener
        const incomingMailColRef = collection(db, `artifacts/${appId}/users/${userId}/incomingMail`);
        const qIncomingMail = query(incomingMailColRef);
        unsubscribeIncomingMail = onSnapshot(qIncomingMail, (snapshot) => {
            allIncomingMailData = []; // Store for filtering
            snapshot.forEach(doc => {
                allIncomingMailData.push({ id: doc.id, ...doc.data() });
            });
            displayIncomingMail(allIncomingMailData); // Display all by default
        }, (error) => {
            console.error("Error fetching incoming mail (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات البريد الوارد.", 'error');
        });

        // Outgoing Mail Listener
        const outgoingMailColRef = collection(db, `artifacts/${appId}/users/${userId}/outgoingMail`);
        const qOutgoingMail = query(outgoingMailColRef);
        unsubscribeOutgoingMail = onSnapshot(qOutgoingMail, (snapshot) => {
            allOutgoingMailData = []; // Store for filtering
            snapshot.forEach(doc => {
                allOutgoingMailData.push({ id: doc.id, ...doc.data() });
            });
            displayOutgoingMail(allOutgoingMailData); // Display all by default
        }, (error) => {
            console.error("Error fetching outgoing mail (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات البريد الصادر.", 'error');
        });

        // Outgoing Circulars Listener
        const outgoingCircularsColRef = collection(db, `artifacts/${appId}/users/${userId}/outgoingCirculars`);
        const qOutgoingCirculars = query(outgoingCircularsColRef);
        unsubscribeOutgoingCirculars = onSnapshot(qOutgoingCirculars, (snapshot) => {
            allOutgoingCircularsData = []; // Store for filtering
            snapshot.forEach(doc => {
                allOutgoingCircularsData.push({ id: doc.id, ...doc.data() });
            });
            displayOutgoingCirculars(allOutgoingCircularsData); // Display all by default
        }, (error) => {
            console.error("Error fetching outgoing circulars (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات التعميمات الصادرة.", 'error');
        });

        // Activities Listener
        const activitiesColRef = collection(db, `artifacts/${appId}/users/${userId}/activities`);
        const qActivities = query(activitiesColRef);
        unsubscribeActivities = onSnapshot(qActivities, (snapshot) => {
            allActivitiesData = []; // Store for filtering/display
            snapshot.forEach(doc => {
                allActivitiesData.push({ id: doc.id, ...doc.data() });
            });
            displayActivities(allActivitiesData);
        }, (error) => {
            console.error("Error fetching activities (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات الأنشطة.", 'error');
        });

        // Plans Listener
        const plansColRef = collection(db, `artifacts/${appId}/users/${userId}/plans`);
        const qPlans = query(plansColRef);
        unsubscribePlans = onSnapshot(qPlans, (snapshot) => {
            allPlansData = []; // Store for filtering/display
            snapshot.forEach(doc => {
                allPlansData.push({ id: doc.id, ...doc.data() });
            });
            displayPlans(allPlansData);
        }, (error) => {
            console.error("Error fetching plans (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات الخطط.", 'error');
        });

        // Endowed Properties Listener
        const endowedPropertiesColRef = collection(db, `artifacts/${appId}/users/${userId}/endowedProperties`);
        const qEndowedProperties = query(endowedPropertiesColRef);
        unsubscribeEndowedProperties = onSnapshot(qEndowedProperties, (snapshot) => {
            allEndowedPropertiesData = [];
            snapshot.forEach(doc => {
                allEndowedPropertiesData.push({ id: doc.id, ...doc.data() });
            });
            displayEndowedProperties(allEndowedPropertiesData);
        }, (error) => {
            console.error("Error fetching endowed properties (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات الأملاك الموقوفة.", 'error');
        });

        // Engineering Projects Listener
        const engineeringProjectsColRef = collection(db, `artifacts/${appId}/users/${userId}/engineeringProjects`);
        const qEngineeringProjects = query(engineeringProjectsColRef);
        unsubscribeEngineeringProjects = onSnapshot(qEngineeringProjects, (snapshot) => {
            allEngineeringProjectsData = [];
            snapshot.forEach(doc => {
                allEngineeringProjectsData.push({ id: doc.id, ...doc.data() });
            });
            displayEngineeringProjects(allEngineeringProjectsData);
        }, (error) => {
            console.error("Error fetching engineering projects (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات المشاريع الهندسية.", 'error');
        });

        // Legal Affairs Listener
        const legalAffairsColRef = collection(db, `artifacts/${appId}/users/${userId}/legalAffairs`);
        const qLegalAffairs = query(legalAffairsColRef);
        unsubscribeLegalAffairs = onSnapshot(qLegalAffairs, (snapshot) => {
            allLegalAffairsData = [];
            snapshot.forEach(doc => {
                allLegalAffairsData.push({ id: doc.id, ...doc.data() });
            });
            displayLegalAffairs(allLegalAffairsData);
        }, (error) => {
            console.error("Error fetching legal affairs (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات الشؤون القانونية.", 'error');
        });

        // Security Clearances Listener
        const securityClearancesColRef = collection(db, `artifacts/${appId}/users/${userId}/securityClearances`);
        const qSecurityClearances = query(securityClearancesColRef);
        unsubscribeSecurityClearances = onSnapshot(qSecurityClearances, (snapshot) => {
            allSecurityClearancesData = [];
            snapshot.forEach(doc => {
                allSecurityClearancesData.push({ id: doc.id, ...doc.data() });
            });
            displaySecurityClearances(allSecurityClearancesData);
        }, (error) => {
            console.error("Error fetching security clearances (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات التصاريح الأمنية.", 'error');
        });

        // IT Assets Listener
        const itAssetsColRef = collection(db, `artifacts/${appId}/users/${userId}/itAssets`);
        const qITAssets = query(itAssetsColRef);
        unsubscribeITAssets = onSnapshot(qITAssets, (snapshot) => {
            allITAssetsData = [];
            snapshot.forEach(doc => {
                allITAssetsData.push({ id: doc.id, ...doc.data() });
            });
            displayITAssets(allITAssetsData);
        }, (error) => {
            console.error("Error fetching IT assets (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات أصول تكنولوجيا المعلومات.", 'error');
        });

        // Research Studies Listener
        const researchStudiesColRef = collection(db, `artifacts/${appId}/users/${userId}/researchStudies`);
        const qResearchStudies = query(researchStudiesColRef);
        unsubscribeResearchStudies = onSnapshot(qResearchStudies, (snapshot) => {
            allResearchStudiesData = [];
            snapshot.forEach(doc => {
                allResearchStudiesData.push({ id: doc.id, ...doc.data() });
            });
            displayResearchStudies(allResearchStudiesData);
        }, (error) => {
            console.error("Error fetching research studies (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات البحوث والدراسات.", 'error');
        });

        // Auditing Reports Listener
        const auditingReportsColRef = collection(db, `artifacts/${appId}/users/${userId}/auditingReports`);
        const qAuditingReports = query(auditingReportsColRef);
        unsubscribeAuditingReports = onSnapshot(qAuditingReports, (snapshot) => {
            allAuditingReportsData = [];
            snapshot.forEach(doc => {
                allAuditingReportsData.push({ id: doc.id, ...doc.data() });
            });
            displayAuditingReports(allAuditingReportsData);
        }, (error) => {
            console.error("Error fetching auditing reports (onSnapshot):", error);
            showMessage("خطأ في جلب بيانات تقارير التدقيق.", 'error');
        });
    };

    // Use a polling mechanism or similar to check for isAuthReady
    const checkAuthAndSetupListeners = setInterval(() => {
        if (isAuthReady && userId && db && isAuthenticated) { // Ensure isAuthenticated is true
            clearInterval(checkAuthAndSetupListeners);
            setupFirestoreListeners();
        } else if (isAuthReady && !isAuthenticated) { // If auth is ready but not authenticated, stop polling
            clearInterval(checkAuthAndSetupListeners);
            console.log("Not authenticated, Firestore listeners not set up.");
        }
    }, 200); // Check every 200ms


    // --- Data Display Functions ---
    function displayInstitutions(institutions) {
        const tbody = document.getElementById('institutionsTableBody');
        tbody.innerHTML = ''; // Clear existing
        if (institutions.length === 0) {
            tbody.innerHTML = '<tr><td colspan="10" class="text-center text-gray-500 py-4">لا توجد مؤسسات مضافة بعد.</td></tr>';
            return;
        }
        institutions.forEach(inst => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${inst.name || 'N/A'}</td>
                <td>${inst.type || 'N/A'}</td>
                <td>${inst.governorate || 'N/A'}</td>
                <td>${inst.location || 'N/A'}</td>
                <td>${inst.capacity || 'N/A'}</td>
                <td>${inst.endowmentType || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${inst.architecturalStatus || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${inst.obstacles || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${inst.needs || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${inst.solutions || 'N/A'}</div></td>
            `;
        });
    }

    function displaySchools(schools) {
        const tbody = document.getElementById('schoolsTableBody');
        tbody.innerHTML = ''; // Clear existing
        if (schools.length === 0) {
            tbody.innerHTML = '<tr><td colspan="12" class="text-center text-gray-500 py-4">لا توجد مدارس مضافة بعد.</td></tr>';
            return;
        }
        schools.forEach(school => {
            const row = tbody.insertRow(); // Create a new row for each school
            const totalPrimaryMale = school.studentPrimaryMale || 0;
            const totalPrimaryFemale = school.studentPrimaryFemale || 0;
            const totalIntermediateMale = school.studentIntermediateMale || 0;
            const totalIntermediateFemale = school.studentIntermediateFemale || 0;
            const totalSecondaryMale = school.studentSecondaryMale || 0;
            const totalSecondaryFemale = school.studentSecondaryFemale || 0;

            const totalMaleStudents = totalPrimaryMale + totalIntermediateMale + totalSecondaryMale;
            const totalFemaleStudents = totalPrimaryFemale + totalIntermediateFemale + totalSecondaryFemale;

            row.innerHTML = `
                <td>${school.name || 'N/A'}</td>
                <td>${school.type || 'N/A'}</td>
                <td>${school.governorate || 'N/A'}</td>
                <td>${school.location || 'N/A'}</td>
                <td>${totalMaleStudents}</td>
                <td>${totalFemaleStudents}</td>
                <td>${school.classCount || 'N/A'}</td>
                <td>${school.affiliation || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${school.architecturalStatus || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${school.obstacles || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${school.needs || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${school.proposedSolutions || 'N/A'}</div></td>
            `;
        });
    }

    function displayAdministrativeResources(adminResources) {
        const tbody = document.getElementById('administrativeResourcesTableBody');
        tbody.innerHTML = ''; // Clear existing
        if (adminResources.length === 0) {
            tbody.innerHTML = '<tr><td colspan="10" class="text-center text-gray-500 py-4">لا توجد بيانات للموارد الإدارية مضافة بعد.</td></tr>';
            return;
        }
        adminResources.forEach(res => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${res.employeeName || 'N/A'}</td>
                <td>${res.position || 'N/A'}</td>
                <td>${res.governorate || 'N/A'}</td>
                <td>${res.appointmentDate || 'N/A'}</td>
                <td>${res.leaveStatus || 'N/A'}</td>
                <td>${res.leaveType || 'N/A'}</td>
                <td>${res.jobGrade || 'N/A'}</td>
                <td>${res.jobCategory || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${res.documents || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${res.notes || 'N/A'}</div></td>
            `;
        });
    }

    // Display Citizen Complaints
    function displayCitizenComplaints(complaintsData) {
        const tbody = document.getElementById('citizenComplaintsTableBody');
        tbody.innerHTML = '';
        if (complaintsData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="7" class="text-center text-gray-500 py-4">لا توجد شكاوى مواطنين مضافة بعد.</td></tr>';
            return;
        }
        complaintsData.forEach(complaint => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${complaint.complaintNumber || 'N/A'}</td>
                <td>${complaint.complaintDate || 'N/A'}</td>
                <td>${complaint.complainantName || 'N/A'}</td>
                <td>${complaint.governorate || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${complaint.complaintSubject || 'N/A'}</div></td>
                <td>${complaint.complaintStatus || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${complaint.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayIncomingMail(mailData) {
        const tbody = document.getElementById('incomingMailTableBody');
        tbody.innerHTML = ''; // Clear existing
        if (mailData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="7" class="text-center text-gray-500 py-4">لا توجد بيانات للبريد الوارد مضافة بعد.</td></tr>';
            return;
        }
        mailData.forEach(mail => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${mail.letterNumber || 'N/A'}</td>
                <td>${mail.letterDate || 'N/A'}</td>
                <td>${mail.sender || 'N/A'}</td>
                <td>${mail.governorate || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${mail.subject || 'N/A'}</div></td>
                <td>${mail.followupStatus || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${mail.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayOutgoingMail(mailData) {
        const tbody = document.getElementById('outgoingMailTableBody');
        tbody.innerHTML = ''; // Clear existing
        if (mailData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="7" class="text-center text-gray-500 py-4">لا توجد بيانات للبريد الصادر مضافة بعد.</td></tr>';
            return;
        }
        mailData.forEach(mail => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${mail.letterNumber || 'N/A'}</td>
                <td>${mail.letterDate || 'N/A'}</td>
                <td>${mail.recipient || 'N/A'}</td>
                <td>${mail.governorate || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${mail.subject || 'N/A'}</div></td>
                <td>${mail.followupStatus || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${mail.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayOutgoingCirculars(circularsData) {
        const tbody = document.getElementById('outgoingCircularsTableBody');
        tbody.innerHTML = ''; // Clear existing
        if (circularsData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="7" class="text-center text-gray-500 py-4">لا توجد بيانات للتعميمات الصادرة مضافة بعد.</td></tr>';
            return;
        }
        circularsData.forEach(circ => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${circ.circularNumber || 'N/A'}</td>
                <td>${circ.circularDate || 'N/A'}</td>
                <td>${circ.recipient || 'N/A'}</td>
                <td>${circ.governorate || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${circ.subject || 'N/A'}</div></td>
                <td>${circ.followupStatus || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${circ.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayActivities(activitiesData) {
        const tbody = document.getElementById('activitiesTableBody');
        tbody.innerHTML = '';
        if (activitiesData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="8" class="text-center text-gray-500 py-4">لا توجد أنشطة/فعاليات مضافة بعد.</td></tr>';
            return;
        }
        activitiesData.forEach(activity => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${activity.activityName || 'N/A'}</td>
                <td>${activity.activityDate || 'N/A'}</td>
                <td>${activity.activityType || 'N/A'}</td>
                <td>${activity.activityGov || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${activity.participants || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${activity.resourcesUsed || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${activity.results || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${activity.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayPlans(plansData) {
        const tbody = document.getElementById('plansTableBody');
        tbody.innerHTML = '';
        if (plansData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="8" class="text-center text-gray-500 py-4">لا توجد خطط مضافة بعد.</td></tr>';
            return;
        }
        plansData.forEach(plan => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${plan.planName || 'N/A'}</td>
                <td>${plan.planType || 'N/A'}</td>
                <td>${plan.planGov || 'N/A'}</td>
                <td>${plan.planStartDate || 'N/A'}</td>
                <td>${plan.planEndDate || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${plan.kpis || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${plan.progress || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${plan.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayEndowedProperties(propertiesData) {
        const tbody = document.getElementById('endowedPropertiesTableBody');
        tbody.innerHTML = '';
        if (propertiesData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="10" class="text-center text-gray-500 py-4">لا توجد أملاك موقوفة أو استثمارات مضافة بعد.</td></tr>';
            return;
        }
        propertiesData.forEach(prop => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${prop.propertyName || 'N/A'}</td>
                <td>${prop.propertyType || 'N/A'}</td>
                <td>${prop.propertyGov || 'N/A'}</td>
                <td>${prop.propertyLocation || 'N/A'}</td>
                <td>${prop.endowerName || 'N/A'}</td>
                <td>${prop.investmentStatus || 'N/A'}</td>
                <td>${prop.investmentType || 'N/A'}</td>
                <td>${prop.contractNumber || 'N/A'}</td>
                <td>${prop.annualRevenue || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${prop.propertyNotes || 'N/A'}</div></td>
            `;
        });
    }

    function displayEngineeringProjects(projectsData) {
        const tbody = document.getElementById('engineeringProjectsTableBody');
        tbody.innerHTML = '';
        if (projectsData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="25" class="text-center text-gray-500 py-4">لا توجد مشاريع هندسية مضافة بعد.</td></tr>';
            return;
        }
        projectsData.forEach(proj => {
            const originalStartDate = proj.projectStartDate ? new Date(proj.projectStartDate) : null;
            const originalEndDate = proj.projectEndDate ? new Date(proj.projectEndDate) : null;
            
            let initialDurationDays = 0;
            if (originalStartDate && originalEndDate) {
                initialDurationDays = Math.ceil((originalEndDate - originalStartDate) / (1000 * 60 * 60 * 24));
            }

            const totalProjectDuration = initialDurationDays +
                                         (proj.extendedPeriodsDays || 0) +
                                         (proj.totalChangeOrdersDuration || 0);
            
            const totalProjectBudget = (proj.projectBudget || 0) + (proj.totalChangeOrdersAmount || 0);

            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${proj.projectName || 'N/A'}</td>
                <td>${proj.projectType || 'N/A'}</td>
                <td>${proj.projectGov || 'N/A'}</td>
                <td>${proj.projectLocation || 'N/A'}</td>
                <td>${proj.projectStatus || 'N/A'}</td>
                <td>${proj.projectBudget || 'N/A'}</td>
                <td>${totalProjectBudget.toLocaleString('ar-IQ')}</td> <!-- Display total budget -->
                <td>${proj.projectStartDate || 'N/A'}</td>
                <td>${proj.projectEndDate || 'N/A'}</td>
                <td>${totalProjectDuration}</td> <!-- Display total duration -->
                <td>${proj.projectContractor || 'N/A'}</td>
                <td>${proj.supervisingEngineer || 'N/A'}</td>
                <td>${proj.projectDocuments || 'N/A'}</td>
                <td>${proj.progressPercentage || 'N/A'}</td>
                <td>${proj.extendedPeriodsDays || 'N/A'}</td>
                <td>${proj.totalChangeOrdersDuration || 'N/A'}</td>
                <td>${(proj.totalChangeOrdersAmount ? proj.totalChangeOrdersAmount.toLocaleString('ar-IQ') : 'N/A')}</td>
                <td>${proj.grantedAdvancesCount || 'N/A'}</td>
                <td>${proj.grantedAdvancesAmount ? proj.grantedAdvancesAmount.toLocaleString('ar-IQ') : 'N/A'}</td>
                <td>${proj.operationalAdvancesCount || 'N/A'}</td>
                <td>${proj.operationalAdvancesAmount ? proj.operationalAdvancesAmount.toLocaleString('ar-IQ') : 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${proj.delayFinesAndReasons || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${proj.projectObstacles || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${proj.projectSolutions || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${proj.projectNotes || 'N/A'}</div></td>
            `;
        });
    }

    function displayLegalAffairs(legalAffairsData) {
        const tbody = document.getElementById('legalAffairsTableBody');
        tbody.innerHTML = '';
        if (legalAffairsData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="9" class="text-center text-gray-500 py-4">لا توجد بيانات للشؤون القانونية مضافة بعد.</td></tr>';
            return;
        }
        legalAffairsData.forEach(affair => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${affair.caseContractName || 'N/A'}</td>
                <td>${affair.type || 'N/A'}</td>
                <td>${affair.governorate || 'N/A'}</td>
                <td>${affair.startDate || 'N/A'}</td>
                <td>${affair.endDate || 'N/A'}</td>
                <td>${affair.involvedParty || 'N/A'}</td>
                <td>${affair.status || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${affair.documents || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${affair.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displaySecurityClearances(clearancesData) {
        const tbody = document.getElementById('securityClearancesTableBody');
        tbody.innerHTML = '';
        if (clearancesData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="7" class="text-center text-gray-500 py-4">لا توجد تصاريح أمنية مضافة بعد.</td></tr>';
            return;
        }
        clearancesData.forEach(clearance => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${clearance.clearanceNumber || 'N/A'}</td>
                <td>${clearance.clearanceType || 'N/A'}</td>
                <td>${clearance.issueDate || 'N/A'}</td>
                <td>${clearance.expiryDate || 'N/A'}</td>
                <td>${clearance.holderName || 'N/A'}</td>
                <td>${clearance.accessLevel || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${clearance.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayITAssets(assetsData) {
        const tbody = document.getElementById('itAssetsTableBody');
        tbody.innerHTML = '';
        if (assetsData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="7" class="text-center text-gray-500 py-4">لا توجد أصول تكنولوجيا معلومات مضافة بعد.</td></tr>';
            return;
        }
        assetsData.forEach(asset => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${asset.assetName || 'N/A'}</td>
                <td>${asset.assetType || 'N/A'}</td>
                <td>${asset.serialNumber || 'N/A'}</td>
                <td>${asset.acquisitionDate || 'N/A'}</td>
                <td>${asset.status || 'N/A'}</td>
                <td>${asset.location || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${asset.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayResearchStudies(studiesData) {
        const tbody = document.getElementById('researchStudiesTableBody');
        tbody.innerHTML = '';
        if (studiesData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="9" class="text-center text-gray-500 py-4">لا توجد بحوث أو دراسات مضافة بعد.</td></tr>';
            return;
        }
        studiesData.forEach(study => {
            const row = tbody.insertRow();
            const dimensions = (study.libraryLength || 0) + 'x' + (study.libraryWidth || 0) + 'x' + (study.libraryHeight || 0) + ' م';
            row.innerHTML = `
                <td>${study.researchTitle || 'N/A'}</td>
                <td>${study.researchAuthor || 'N/A'}</td>
                <td>${study.publicationDate || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${study.researchSummary || 'N/A'}</div></td>
                <td>${study.libraryName || 'N/A'}</td>
                <td>${dimensions || 'N/A'}</td>
                <td>${study.numBooks || 'N/A'}</td>
                <td>${study.numReferences || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${study.notes || 'N/A'}</div></td>
            `;
        });
    }

    function displayAuditingReports(reportsData) {
        const tbody = document.getElementById('auditingReportsTableBody');
        tbody.innerHTML = '';
        if (reportsData.length === 0) {
            tbody.innerHTML = '<tr><td colspan="8" class="text-center text-gray-500 py-4">لا توجد تقارير تدقيق مضافة بعد.</td></tr>';
            return;
        }
        reportsData.forEach(report => {
            const row = tbody.insertRow();
            row.innerHTML = `
                <td>${report.reportNumber || 'N/A'}</td>
                <td>${report.reportDate || 'N/A'}</td>
                <td>${report.auditingEntity || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${report.observations || 'N/A'}</div></td>
                <td><div style="max-height: 100px; overflow-y: auto;">${report.recommendations || 'N/A'}</div></td>
                <td>${report.followupStatus || 'N/A'}</td>
                <td>${report.transactionsCount || 'N/A'}</td>
                <td><div style="max-height: 100px; overflow-y: auto;">${report.notes || 'N/A'}</div></td>
            `;
        });
    }

    // --- Add Data Functions ---
    document.getElementById('addInstitutionForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة المؤسسة: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const name = document.getElementById('institutionName').value;
        const type = document.getElementById('institutionType').value;
        const governorate = document.getElementById('institutionGov').value;
        const location = document.getElementById('institutionLocation').value;
        const capacity = parseInt(document.getElementById('institutionCapacity').value) || 0;
        const endowmentType = document.getElementById('institutionEndowmentType').value;
        const architecturalStatus = document.getElementById('institutionArchitecturalStatus').value;
        const obstacles = document.getElementById('institutionObstacles').value;
        const needs = document.getElementById('institutionNeeds').value;
        const solutions = document.getElementById('institutionSolutions').value;


        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/institutions`), {
                name, type, governorate, location, capacity,
                endowmentType, architecturalStatus, obstacles, needs, solutions,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة المؤسسة بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding institution: ", e);
            showMessage("خطأ في إضافة المؤسسة.", 'error');
        }
    });

    document.getElementById('addSchoolForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة المدرسة: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const name = document.getElementById('schoolName').value;
        const type = document.getElementById('schoolType').value;
        const governorate = document.getElementById('schoolGov').value;
        const location = document.getElementById('schoolLocation').value;
        const studentPrimaryMale = parseInt(document.getElementById('studentPrimaryMale').value) || 0;
        const studentPrimaryFemale = parseInt(document.getElementById('studentPrimaryFemale').value) || 0;
        const studentIntermediateMale = parseInt(document.getElementById('studentIntermediateMale').value) || 0;
        const studentIntermediateFemale = parseInt(document.getElementById('studentIntermediateFemale').value) || 0;
        const studentSecondaryMale = parseInt(document.getElementById('studentSecondaryMale').value) || 0;
        const studentSecondaryFemale = parseInt(document.getElementById('studentSecondaryFemale').value) || 0;
        const classCount = parseInt(document.getElementById('schoolClassCount').value) || 0;
        const affiliation = document.getElementById('schoolAffiliation').value;
        const architecturalStatus = document.getElementById('schoolArchitecturalStatus').value;
        const obstacles = document.getElementById('schoolObstacles').value;
        const needs = document.getElementById('schoolNeeds').value;
        const proposedSolutions = document.getElementById('schoolProposedSolutions').value;


        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/schools`), {
                name, type, governorate, location,
                studentPrimaryMale, studentPrimaryFemale,
                studentIntermediateMale, studentIntermediateFemale,
                studentSecondaryMale, studentSecondaryFemale,
                classCount,
                affiliation, architecturalStatus, obstacles, needs, proposedSolutions,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة المدرسة بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding school: ", e);
            showMessage("خطأ في إضافة المدرسة.", 'error');
        }
    });

    document.getElementById('addAdministrativeResourceForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة الموظف: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const employeeName = document.getElementById('adminEmployeeName').value;
        const position = document.getElementById('adminPosition').value;
        const governorate = document.getElementById('adminGov').value;
        const appointmentDate = document.getElementById('adminAppointmentDate').value;
        const leaveStatus = document.getElementById('adminLeaveStatus').value;
        const leaveType = document.getElementById('adminLeaveType').value;
        const jobGrade = document.getElementById('adminJobGrade').value;
        const jobCategory = document.getElementById('adminJobCategory').value;
        const documentsFileName = document.getElementById('adminDocumentsUpload').value;
        const notes = document.getElementById('adminNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/administrativeResources`), {
                employeeName, position, governorate, appointmentDate, leaveStatus, leaveType, jobGrade, jobCategory, documents: documentsFileName, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة الموظف الإداري بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding administrative resource: ", e);
            showMessage("خطأ في إضافة الموظف الإداري.", 'error');
        }
    });

    // Add Citizen Complaint Form Submission
    document.getElementById('addCitizenComplaintForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة الشكوى: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const complaintNumber = document.getElementById('complaintNumber').value;
        const complaintDate = document.getElementById('complaintDate').value;
        const complainantName = document.getElementById('complainantName').value;
        const governorate = document.getElementById('complaintGov').value;
        const complaintSubject = document.getElementById('complaintSubject').value;
        const complaintStatus = document.getElementById('complaintStatus').value;
        const notes = document.getElementById('complaintNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/citizenComplaints`), {
                complaintNumber, complaintDate, complainantName, governorate, complaintSubject, complaintStatus, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة الشكوى بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding citizen complaint: ", e);
            showMessage("خطأ في إضافة الشكوى.", 'error');
        }
    });

    document.getElementById('addIncomingMailForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة الكتاب الوارد: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const letterNumber = document.getElementById('incomingMailLetterNumber').value;
        const letterDate = document.getElementById('incomingMailLetterDate').value;
        const sender = document.getElementById('incomingMailSender').value;
        const governorate = document.getElementById('incomingMailGov').value;
        const subject = document.getElementById('incomingMailSubject').value;
        const followupStatus = document.getElementById('incomingMailFollowupStatus').value;
        const notes = document.getElementById('incomingMailNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/incomingMail`), {
                letterNumber, letterDate, sender, governorate, subject, followupStatus, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة الكتاب الوارد بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding incoming mail: ", e);
            showMessage("خطأ في إضافة الكتاب الوارد.", 'error');
        }
    });

    document.getElementById('addOutgoingMailForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة الكتاب الصادر: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const letterNumber = document.getElementById('outgoingMailLetterNumber').value;
        const letterDate = document.getElementById('outgoingMailLetterDate').value;
        const recipient = document.getElementById('outgoingMailRecipient').value;
        const governorate = document.getElementById('outgoingMailGov').value;
        const subject = document.getElementById('outgoingMailSubject').value;
        const followupStatus = document.getElementById('outgoingMailFollowupStatus').value;
        const notes = document.getElementById('outgoingMailNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/outgoingMail`), {
                letterNumber, letterDate, recipient, governorate, subject, followupStatus, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة الكتاب الصادر بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding outgoing mail: ", e);
            showMessage("خطأ في إضافة الكتاب الصادر.", 'error');
        }
    });

    document.getElementById('addOutgoingCircularForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة التعميم الصادر: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const circularNumber = document.getElementById('outgoingCircularNumber').value;
        const circularDate = document.getElementById('outgoingCircularDate').value;
        const recipient = document.getElementById('outgoingCircularRecipient').value;
        const governorate = document.getElementById('outgoingCircularGov').value;
        const subject = document.getElementById('outgoingCircularSubject').value;
        const followupStatus = document.getElementById('outgoingCircularFollowupStatus').value;
        const notes = document.getElementById('outgoingCircularNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/outgoingCirculars`), {
                circularNumber, circularDate, recipient, governorate, subject, followupStatus, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة التعميم الصادر بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding outgoing circular: ", e);
            showMessage("خطأ في إضافة التعميم الصادر.", 'error');
        }
    });

    document.getElementById('addActivityForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة النشاط: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const activityName = document.getElementById('activityName').value;
        const activityDate = document.getElementById('activityDate').value;
        const activityType = document.getElementById('activityType').value;
        const activityGov = document.getElementById('activityGov').value;
        const participants = document.getElementById('activityParticipants').value;
        const resourcesUsed = document.getElementById('activityResources').value;
        const results = document.getElementById('activityResults').value;
        const notes = document.getElementById('activityNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/activities`), {
                activityName, activityDate, activityType, activityGov, participants, resourcesUsed, results, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة النشاط/الفعالية بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding activity: ", e);
            showMessage("خطأ في إضافة النشاط/الفعالية.", 'error');
        }
    });

    document.getElementById('addPlanForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة الخطة: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const planName = document.getElementById('planName').value;
        const planType = document.getElementById('planType').value;
        const planGov = document.getElementById('planGov').value;
        const planStartDate = document.getElementById('planStartDate').value;
        const planEndDate = document.getElementById('planEndDate').value;
        const kpis = document.getElementById('planKPIs').value;
        const progress = document.getElementById('planProgress').value;
        const notes = document.getElementById('planNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/plans`), {
                planName, planType, planGov, planStartDate, planEndDate, kpis, progress, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة الخطة بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding plan: ", e);
            showMessage("خطأ في إضافة الخطة.", 'error');
        }
    });

    document.getElementById('addEndowedPropertyForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة العقار: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const propertyName = document.getElementById('propertyName').value;
        const propertyType = document.getElementById('propertyType').value;
        const propertyGov = document.getElementById('propertyGov').value;
        const propertyLocation = document.getElementById('propertyLocation').value;
        const endowmentPropertyType = document.getElementById('endowmentPropertyType').value;
        const endowerName = document.getElementById('endowerName').value;
        const propertyLegalStatus = document.getElementById('propertyLegalStatus').value;
        const investmentStatus = document.getElementById('investmentStatus').value;
        const investmentType = document.getElementById('investmentType').value;
        const contractNumber = document.getElementById('contractNumber').value;
        const contractStartDate = document.getElementById('contractStartDate').value;
        const contractEndDate = document.getElementById('contractEndDate').value;
        const annualRevenue = parseFloat(document.getElementById('annualRevenue').value) || 0;
        const propertyNotes = document.getElementById('propertyNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/endowedProperties`), {
                propertyName, propertyType, propertyGov, propertyLocation, endowmentPropertyType, endowerName, propertyLegalStatus,
                investmentStatus, investmentType, contractNumber, contractStartDate, contractEndDate, annualRevenue, propertyNotes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة العقار/الاستثمار بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding endowed property: ", e);
            showMessage("خطأ في إضافة العقار/الاستثمار.", 'error');
        }
    });

    document.getElementById('addEngineeringProjectForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة المشروع: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const projectName = document.getElementById('projectName').value;
        const projectType = document.getElementById('projectType').value;
        const projectGov = document.getElementById('projectGov').value;
        const projectLocation = document.getElementById('projectLocation').value;
        const projectStatus = document.getElementById('projectStatus').value;
        const projectBudget = parseFloat(document.getElementById('projectBudget').value) || 0;
        const projectStartDate = document.getElementById('projectStartDate').value;
        const projectEndDate = document.getElementById('projectEndDate').value;
        const projectContractor = document.getElementById('projectContractor').value;
        const supervisingEngineer = document.getElementById('supervisingEngineer').value;
        const projectDocuments = document.getElementById('projectDocuments').value;
        const progressPercentage = parseFloat(document.getElementById('progressPercentage').value) || 0;
        const extendedPeriodsDays = parseInt(document.getElementById('extendedPeriodsDays').value) || 0;
        
        // Consolidated Change Orders
        const totalChangeOrdersDuration = parseInt(document.getElementById('totalChangeOrdersDuration').value) || 0;
        const totalChangeOrdersAmount = parseFloat(document.getElementById('totalChangeOrdersAmount').value) || 0;

        const grantedAdvancesCount = parseInt(document.getElementById('grantedAdvancesCount').value) || 0;
        const grantedAdvancesAmount = parseFloat(document.getElementById('grantedAdvancesAmount').value) || 0;
        const operationalAdvancesCount = parseInt(document.getElementById('operationalAdvancesCount').value) || 0;
        const operationalAdvancesAmount = parseFloat(document.getElementById('operationalAdvancesAmount').value) || 0;
        const delayFinesAndReasons = document.getElementById('delayFinesAndReasons').value;
        const projectObstacles = document.getElementById('projectObstacles').value;
        const projectSolutions = document.getElementById('projectSolutions').value;
        const projectNotes = document.getElementById('projectNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/engineeringProjects`), {
                projectName, projectType, projectGov, projectLocation, projectStatus, projectBudget,
                projectStartDate, projectEndDate, projectContractor, supervisingEngineer, projectDocuments,
                progressPercentage, extendedPeriodsDays,
                totalChangeOrdersDuration, totalChangeOrdersAmount,
                grantedAdvancesCount, grantedAdvancesAmount, operationalAdvancesCount, operationalAdvancesAmount,
                delayFinesAndReasons,
                projectObstacles, projectSolutions, projectNotes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة المشروع الهندسي بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding engineering project: ", e);
            showMessage("خطأ في إضافة المشروع الهندسي.", 'error');
        }
    });

    document.getElementById('addLegalAffairForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة الشأن القانوني: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const caseContractName = document.getElementById('legalCaseContractName').value;
        const type = document.getElementById('legalAffairType').value;
        const governorate = document.getElementById('legalAffairGov').value;
        const startDate = document.getElementById('legalAffairStartDate').value;
        const endDate = document.getElementById('legalAffairEndDate').value;
        const involvedParty = document.getElementById('legalAffairInvolvedParty').value;
        const status = document.getElementById('legalAffairStatus').value;
        const documents = document.getElementById('legalAffairDocuments').value;
        const notes = document.getElementById('legalAffairNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/legalAffairs`), {
                caseContractName, type, governorate, startDate, endDate, involvedParty, status, documents, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة الشأن القانوني بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding legal affair: ", e);
            showMessage("خطأ في إضافة الشأن القانوني.", 'error');
        }
    });

    document.getElementById('addSecurityClearanceForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة التصريح الأمني: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const clearanceNumber = document.getElementById('clearanceNumber').value;
        const clearanceType = document.getElementById('clearanceType').value;
        const issueDate = document.getElementById('clearanceIssueDate').value;
        const expiryDate = document.getElementById('clearanceExpiryDate').value;
        const holderName = document.getElementById('clearanceHolderName').value;
        const accessLevel = document.getElementById('clearanceAccessLevel').value;
        const notes = document.getElementById('clearanceNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/securityClearances`), {
                clearanceNumber, clearanceType, issueDate, expiryDate, holderName, accessLevel, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة التصريح الأمني بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding security clearance: ", e);
            showMessage("خطأ في إضافة التصريح الأمني.", 'error');
        }
    });

    document.getElementById('addITAssetForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة الأصل التقني: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const assetName = document.getElementById('itAssetName').value;
        const assetType = document.getElementById('itAssetType').value;
        const serialNumber = document.getElementById('itAssetSerialNumber').value;
        const acquisitionDate = document.getElementById('itAssetAcquisitionDate').value;
        const status = document.getElementById('itAssetStatus').value;
        const location = document.getElementById('itAssetLocation').value;
        const notes = document.getElementById('itAssetNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/itAssets`), {
                assetName, assetType, serialNumber, acquisitionDate, status, location, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة الأصل التقني بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding IT asset: ", e);
            showMessage("خطأ في إضافة الأصل التقني.", 'error');
        }
    });

    document.getElementById('addResearchStudyForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة البحث/الدراسة: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const researchTitle = document.getElementById('researchTitle').value;
        const researchAuthor = document.getElementById('researchAuthor').value;
        const publicationDate = document.getElementById('researchPublicationDate').value;
        const researchSummary = document.getElementById('researchSummary').value;
        const libraryName = document.getElementById('libraryName').value;
        const libraryLength = parseFloat(document.getElementById('libraryLength').value) || 0;
        const libraryWidth = parseFloat(document.getElementById('libraryWidth').value) || 0;
        const libraryHeight = parseFloat(document.getElementById('libraryHeight').value) || 0;
        const numBooks = parseInt(document.getElementById('numBooks').value) || 0;
        const numReferences = parseInt(document.getElementById('numReferences').value) || 0;
        const notes = document.getElementById('researchNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/researchStudies`), {
                researchTitle, researchAuthor, publicationDate, researchSummary,
                libraryName, libraryLength, libraryWidth, libraryHeight, numBooks, numReferences, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة البحث/الدراسة بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding research study: ", e);
            showMessage("خطأ في إضافة البحث/الدراسة.", 'error');
        }
    });

    document.getElementById('addAuditingReportForm').addEventListener('submit', async (e) => {
        e.preventDefault();
        if (!userId) {
            showMessage("فشل إضافة تقرير التدقيق: المستخدم غير مسجل الدخول.", 'error');
            return;
        }
        const reportNumber = document.getElementById('auditingReportNumber').value;
        const reportDate = document.getElementById('auditingReportDate').value;
        const auditingEntity = document.getElementById('auditingEntity').value;
        const observations = document.getElementById('auditingObservations').value;
        const recommendations = document.getElementById('auditingRecommendations').value;
        const followupStatus = document.getElementById('auditingFollowupStatus').value;
        const transactionsCount = parseInt(document.getElementById('auditedTransactionsCount').value) || 0;
        const notes = document.getElementById('auditingNotes').value;

        try {
            await addDoc(collection(db, `artifacts/${appId}/users/${userId}/auditingReports`), {
                reportNumber, reportDate, auditingEntity, observations, recommendations, followupStatus, transactionsCount, notes,
                createdAt: serverTimestamp()
            });
            showMessage('تمت إضافة تقرير التدقيق بنجاح!', 'success');
            e.target.reset();
        } catch (e) {
            console.error("Error adding auditing report: ", e);
            showMessage("خطأ في إضافة تقرير التدقيق.", 'error');
        }
    });


    // --- Search Functions ---
    document.getElementById('incomingMailSearchQuery').addEventListener('input', () => {
        const query = document.getElementById('incomingMailSearchQuery').value.toLowerCase();
        const filteredData = allIncomingMailData.filter(mail => {
            return (mail.letterNumber && mail.letterNumber.toLowerCase().includes(query)) ||
                   (mail.letterDate && mail.letterDate.toLowerCase().includes(query)) ||
                   (mail.subject && mail.subject.toLowerCase().includes(query)) ||
                   (mail.sender && mail.sender.toLowerCase().includes(query));
        });
        displayIncomingMail(filteredData);
    });

    document.getElementById('outgoingMailSearchQuery').addEventListener('input', () => {
        const query = document.getElementById('outgoingMailSearchQuery').value.toLowerCase();
        const filteredData = allOutgoingMailData.filter(mail => {
            return (mail.letterNumber && mail.letterNumber.toLowerCase().includes(query)) ||
                   (mail.letterDate && mail.letterDate.toLowerCase().includes(query)) ||
                   (mail.subject && mail.subject.toLowerCase().includes(query)) ||
                   (mail.recipient && mail.recipient.toLowerCase().includes(query));
        });
        displayOutgoingMail(filteredData);
    });

    document.getElementById('outgoingCircularSearchQuery').addEventListener('input', () => {
        const query = document.getElementById('outgoingCircularSearchQuery').value.toLowerCase();
        const filteredData = allOutgoingCircularsData.filter(circ => {
            return (circ.circularNumber && circ.circularNumber.toLowerCase().includes(query)) ||
                   (circ.circularDate && circ.circularDate.toLowerCase().includes(query)) ||
                   (circ.subject && circ.subject.toLowerCase().includes(query)) ||
                   (circ.recipient && circ.recipient.toLowerCase().includes(query));
        });
        displayOutgoingCirculars(filteredData);
    });


    // --- Generate Comprehensive Reports Function ---
    document.getElementById('generateReportBtn').addEventListener('click', async () => {
        if (!userId) {
            showMessage("فشل توليد التقرير: المستخدم غير مسجل الدخول.", 'error');
            return;
        }

        const reportOutputs = {
            'البصرة': document.getElementById('basraReportOutput'),
            'ميسان': document.getElementById('maysanReportOutput'),
            'ذي قار': document.getElementById('dhiQarReportOutput')
        };
        const spinner = document.getElementById('reportSpinner');

        // Initialize all report output areas
        for (const gov in reportOutputs) {
            reportOutputs[gov].innerHTML = `<h4 class="text-xl font-semibold text-gray-700 mb-3">تقرير مديرية ${gov}:</h4><p class="text-gray-600">جاري توليد التقرير، يرجى الانتظار...</p>`;
        }
        spinner.classList.remove('hidden');

        try {
            // Fetch all data from all collections
            const collections = [
                'institutions', 'schools', 'administrativeResources', 'citizenComplaints',
                'incomingMail', 'outgoingMail', 'outgoingCirculars', 'activities',
                'plans', 'endowedProperties', 'engineeringProjects', 'legalAffairs',
                'securityClearances', 'itAssets', 'researchStudies', 'auditingReports'
            ];

            const allFetchedData = {};
            for (const colName of collections) {
                const snapshot = await getDocs(collection(db, `artifacts/${appId}/users/${userId}/${colName}`));
                allFetchedData[colName] = [];
                snapshot.forEach(doc => allFetchedData[colName].push(doc.data()));
            }

            // Group data by governorate
            const dataByGovernorate = {
                'البصرة': {},
                'ميسان': {},
                'ذي قار': {}
            };

            for (const colName in allFetchedData) {
                allFetchedData[colName].forEach(item => {
                    const gov = item.governorate;
                    if (dataByGovernorate[gov]) {
                        if (!dataByGovernorate[gov][colName]) {
                            dataByGovernorate[gov][colName] = [];
                        }
                        dataByGovernorate[gov][colName].push(item);
                    }
                });
            }

            const governorates = ['البصرة', 'ميسان', 'ذي قار'];
            for (const gov of governorates) {
                const currentGovData = dataByGovernorate[gov];
                if (Object.keys(currentGovData).length === 0 || collections.every(col => !currentGovData[col] || currentGovData[col].length === 0)) {
                     reportOutputs[gov].innerHTML = `<h4 class="text-xl font-semibold text-gray-700 mb-3">تقرير مديرية ${gov}:</h4><p class="text-red-500">لا توجد بيانات مسجلة لمديرية ${gov} لتوليد التقرير.</p>`;
                     continue;
# r.eng.south.department
