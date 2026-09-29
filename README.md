# Simple To-Do UI (Multi-Section Productivity Dashboard)

**Author:** Shanmukhapriya  
**Track:** Android Development Track  

A modern, card-styled Android user interface built using XML for a productivity app. It features an interactive task input section, a three-column dashboard layout (My Tasks, Notes, and To-Do Lists), and a bottom status indicator for saved and completed items.

---

## 📌 Project Overview

* **Title:** Simple To-Do UI
* **Author:** Shanmukhapriya
* **Track:** Android Development Track
* **Language/Tools:** Android Studio, XML, Kotlin

---

## ✨ Features

* **Modern Card View Layout:** Wrapped inside an elevated `CardView` with rounded corners for a clean, material UI aesthetic.
* **Header & Item Counter:** Displays title and a live item badge container.
* **Quick Task Input:** Rounded input field paired with a styled `MaterialButton` for fast task addition.
* **3-Column Organized Dashboard:**
  * **✅ My Tasks:** Dedicated list section for personal tasks.
  * **📝 Notes:** Section for quick notes and reminders.
  * **📋 To-Do Lists:** Categorized section for structured to-do items.
* **Bottom Status Bar:** Displays status indicators for **📁 Saved Tasks** and **✔ Completed Tasks** side by side.
* **Clean Design Mode:** Configured with `tools:itemCount="0"` to keep the design view clean and free of sample layout placeholders.

---

## 🛠 Layout XML Code (`activity_main.xml`)

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.cardview.widget.CardView 
    xmlns:android="[http://schemas.android.com/apk/res/android](http://schemas.android.com/apk/res/android)"
    xmlns:app="[http://schemas.android.com/apk/res-auto](http://schemas.android.com/apk/res-auto)"
    xmlns:tools="[http://schemas.android.com/tools](http://schemas.android.com/tools)"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_margin="16dp"
    app:cardCornerRadius="16dp"
    app:cardElevation="6dp">

    <LinearLayout android:background="#FAFAFA" android:layout_height="match_parent" android:layout_width="match_parent" android:orientation="vertical" android:padding="20dp">

        <!-- Main Header -->
        <LinearLayout android:gravity="center_vertical" android:layout_height="wrap_content" android:layout_marginBottom="16dp" android:layout_width="match_parent" android:orientation="horizontal">

            <TextView android:id="@+id/tvTitle" android:layout_height="wrap_content" android:layout_weight="1" android:layout_width="0dp" android:text="Dashboard" android:textColor="#1E293B" android:textSize="28sp" android:textStyle="bold"/>

            <TextView android:background="@drawable/shape_badge" android:id="@+id/tvTaskCount" android:layout_height="wrap_content" android:layout_width="wrap_content" android:paddingHorizontal="12dp" android:paddingVertical="4dp" android:text="0 Items" android:textColor="#2563EB" android:textSize="12sp" android:textStyle="bold"/>
        </LinearLayout>

        <!-- New Task Input Section -->
        <androidx.cardview.widget.CardView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="16dp"
            app:cardCornerRadius="12dp"
            app:cardElevation="2dp"
            app:cardBackgroundColor="#FFFFFF">

            <LinearLayout android:gravity="center_vertical" android:layout_height="wrap_content" android:layout_width="match_parent" android:orientation="horizontal" android:padding="8dp">

                <EditText android:background="@null" android:hint="Type a new item..." android:id="@+id/etTaskInput" android:inputType="textCapSentences" android:layout_height="wrap_content" android:layout_weight="1" android:layout_width="0dp" android:padding="12dp" android:textColor="#334155" android:textColorHint="#94A3B8" android:textSize="15sp"/>

                <com.google.android.material.button.MaterialButton
                    android:id="@+id/btnAddTask"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="Add"
                    android:textAllCaps="false"
                    app:cornerRadius="8dp"
                    app:backgroundTint="#2563EB" />
            </LinearLayout>
        </androidx.cardview.widget.CardView>

        <!-- Divider Line -->
        <View android:background="#CBD5E1" android:id="@+id/dividerLine" android:layout_height="2dp" android:layout_marginBottom="16dp" android:layout_width="match_parent"/>

        <!-- 3-Column Layout: My Tasks | Notes | To-Do Lists -->
        <LinearLayout android:layout_height="0dp" android:layout_weight="1" android:layout_width="match_parent" android:orientation="horizontal">

            <!-- 1. My Tasks Section -->
            <LinearLayout android:layout_height="match_parent" android:layout_marginEnd="6dp" android:layout_weight="1" android:layout_width="0dp" android:orientation="vertical">

                <TextView android:layout_height="wrap_content" android:layout_marginBottom="8dp" android:layout_width="wrap_content" android:text="✅ My Tasks" android:textColor="#334155" android:textSize="14sp" android:textStyle="bold"/>

                <androidx.recyclerview.widget.RecyclerView
                    android:id="@+id/rvMyTasksList"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:scrollbars="vertical"
                    tools:itemCount="0" />
            </LinearLayout>

            <!-- Divider 1 -->
            <View android:background="#E2E8F0" android:layout_height="match_parent" android:layout_width="1dp"/>

            <!-- 2. Notes Section -->
            <LinearLayout android:layout_height="match_parent" android:layout_marginEnd="6dp" android:layout_marginStart="6dp" android:layout_weight="1" android:layout_width="0dp" android:orientation="vertical">

                <TextView android:layout_height="wrap_content" android:layout_marginBottom="8dp" android:layout_width="wrap_content" android:text="📝 Notes" android:textColor="#334155" android:textSize="14sp" android:textStyle="bold"/>

                <androidx.recyclerview.widget.RecyclerView
                    android:id="@+id/rvNotesList"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:scrollbars="vertical"
                    tools:itemCount="0" />
            </LinearLayout>

            <!-- Divider 2 -->
            <View android:background="#E2E8F0" android:layout_height="match_parent" android:layout_width="1dp"/>

            <!-- 3. To-Do Lists Section -->
            <LinearLayout android:layout_height="match_parent" android:layout_marginStart="6dp" android:layout_weight="1" android:layout_width="0dp" android:orientation="vertical">

                <TextView android:layout_height="wrap_content" android:layout_marginBottom="8dp" android:layout_width="wrap_content" android:text="📋 To-Do Lists" android:textColor="#334155" android:textSize="14sp" android:textStyle="bold"/>

                <androidx.recyclerview.widget.RecyclerView
                    android:id="@+id/rvToDoList"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:scrollbars="vertical"
                    tools:itemCount="0" />
            </LinearLayout>

        </LinearLayout>

        <!-- Bottom Status Bar -->
        <LinearLayout android:gravity="center_vertical" android:layout_height="wrap_content" android:layout_marginTop="12dp" android:layout_width="match_parent" android:orientation="horizontal" android:paddingTop="8dp">

            <TextView android:id="@+id/tvSavedTasksLabel" android:layout_height="wrap_content" android:layout_weight="1" android:layout_width="0dp" android:text="📁 Saved Tasks" android:textColor="#64748B" android:textSize="14sp" android:textStyle="bold"/>

            <TextView android:id="@+id/tvCompletedTasksLabel" android:layout_height="wrap_content" android:layout_width="wrap_content" android:text="✔ Completed Tasks" android:textColor="#16A34A" android:textSize="14sp" android:textStyle="bold"/>

        </LinearLayout>

    </LinearLayout>
</androidx.cardview.widget.CardView>
