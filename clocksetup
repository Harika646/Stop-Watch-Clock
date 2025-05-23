import tkinter as tk
from datetime import datetime
import time
import threading

class ClockStopwatchApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Clock + Stopwatch App")
        self.root.geometry("400x300")
        self.root.resizable(False, False)

        self.create_widgets()
        self.update_clock()

        self.running = False
        self.counter = 0

    def create_widgets(self):
        # Clock Label
        self.clock_label = tk.Label(self.root, text="", font=("Helvetica", 24), fg="blue")
        self.clock_label.pack(pady=10)

        # Stopwatch Label
        self.stopwatch_label = tk.Label(self.root, text="00:00:00", font=("Helvetica", 30), fg="green")
        self.stopwatch_label.pack(pady=10)

        # Stopwatch Buttons
        btn_frame = tk.Frame(self.root)
        btn_frame.pack(pady=10)

        self.start_btn = tk.Button(btn_frame, text="Start", width=10, command=self.start)
        self.start_btn.grid(row=0, column=0, padx=5)

        self.stop_btn = tk.Button(btn_frame, text="Stop", width=10, command=self.stop)
        self.stop_btn.grid(row=0, column=1, padx=5)

        self.reset_btn = tk.Button(btn_frame, text="Reset", width=10, command=self.reset)
        self.reset_btn.grid(row=0, column=2, padx=5)

    def update_clock(self):
        now = datetime.now().strftime("%H:%M:%S")
        self.clock_label.config(text=f"Current Time: {now}")
        self.root.after(1000, self.update_clock)

    def update_stopwatch(self):
        while self.running:
            time.sleep(1)
            self.counter += 1
            self.display_time()

    def display_time(self):
        hours = self.counter // 3600
        minutes = (self.counter % 3600) // 60
        seconds = self.counter % 60
        self.stopwatch_label.config(text=f"{hours:02}:{minutes:02}:{seconds:02}")

    def start(self):
        if not self.running:
            self.running = True
            threading.Thread(target=self.update_stopwatch, daemon=True).start()

    def stop(self):
        self.running = False

    def reset(self):
        self.running = False
        self.counter = 0
        self.stopwatch_label.config(text="00:00:00")


# Run the application
if __name__ == "__main__":
    root = tk.Tk()
    app = ClockStopwatchApp(root)
    root.mainloop()
