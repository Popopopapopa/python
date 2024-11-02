class Cat:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        self.mood = 50  
        self.satisfaction = 50 

    def pet(self):
        self.mood += 10
        self.satisfaction += 5
        print(f"{self.name} наслаждается лаской! Настроение: {self.mood}, Удовлетворенность: {self.satisfaction}")

    def feed(self):
        self.satisfaction += 15
        print(f"{self.name} поел. Удовлетворенность: {self.satisfaction}")

    def play(self):
        self.mood += 20
        self.satisfaction -= 5
        print(f"{self.name} повеселился! Настроение: {self.mood}, Удовлетворенность: {self.satisfaction}")

    def status(self):
        print(f"{self.name} - Возраст: {self.age}, Настроение: {self.mood}, Удовлетворенность: {self.satisfaction}")






        import random

class Student:
    def __init__(self, name):
        self.name = name
        self.money = 100  
        self.knowledge = 50  
        self.fatigue = 0  
        self.is_alive = True 

    def study(self):
        if self.fatigue < 70:
            self.knowledge += 10
            self.fatigue += 20
            self.money -= 5  
            print(f"{self.name} учится. Знания: {self.knowledge}, Усталость: {self.fatigue}, Деньги: {self.money}")
        else:
            print(f"{self.name} слишком устал, чтобы учиться.")

    def work(self):
        if self.fatigue < 80:
            self.money += 20
            self.fatigue += 30
            print(f"{self.name} работает. Деньги: {self.money}, Усталость: {self.fatigue}")
        else:
            print(f"{self.name} слишком устал, чтобы работать.")

    def rest(self):
        if self.money >= 10:
            self.fatigue -= 30
            self.money -= 10
            if self.fatigue < 0:
                self.fatigue = 0
            print(f"{self.name} отдыхает. Усталость: {self.fatigue}, Деньги: {self.money}")
        else:
            print(f"У {self.name} недостаточно денег для отдыха.")

    def live_day(self):
        if not self.is_alive:
            print(f"{self.name} больше не может продолжать.")
            return

        if self.money < 20:
            print(f"{self.name} вынужден пойти на работу из-за нехватки денег.")
            self.work()

        elif self.knowledge < 50:
            print(f"{self.name} нужно подтянуть знания.")
            self.study()

        elif self.fatigue > 50:
            print(f"{self.name} слишком устал и идет отдыхать.")
            self.rest()

        else:
            action = random.choice(['study', 'work', 'rest'])
            if action == 'study':
                self.study()
            elif action == 'work':
                self.work()
            else:
                self.rest()

        if self.money <= 0 or self.knowledge <= 0 or self.fatigue >= 100:
            self.is_alive = False
            print(f"{self.name} не смог справиться с трудностями.")

    def live_year(self):
        for day in range(1, 366):
            print(f"\nДень {day}")
            self.live_day()
            if not self.is_alive:
                print(f"{self.name} не прожил весь год.")
                break
        if self.is_alive:
            print(f"{self.name} успешно прожил год с деньгами: {self.money}, знаниями: {self.knowledge}, усталостью: {self.fatigue}"
