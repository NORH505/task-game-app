# task-game-app import React, { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Progress } from "@/components/ui/progress";

const App = () => { const [xp, setXp] = useState(80); const [gold, setGold] = useState(350); const [tasks, setTasks] = useState([ { id: 1, title: "هفّة الغال", desc: "أكل المحول", icon: "🗡️" }, { id: 2, title: "البحث الأثاري", desc: "اكتشف المخفية", icon: "📜" }, { id: 3, title: "التدريب على", desc: "تمرينات على الجديدة", icon: "⚔️" }, { id: 4, title: "التدريب السيف", desc: "تمرن على الحركات الجديدة", icon: "🗡️" }, ]);

const completeTask = (id) => { setXp(xp + 100); setGold(gold + 50); setTasks(tasks.filter((task) => task.id !== id)); };

return ( <div className="min-h-screen bg-purple-100 p-4"> <div className="bg-white p-4 rounded-2xl shadow-md mb-4 flex justify-between items-center"> <h1 className="text-2xl font-bold text-orange-600">مغامرات المهام</h1> <div className="text-right"> <div className="text-sm">{xp} / 2200 XP</div> <Progress value={(xp / 2200) * 100} className="w-40" /> </div> <div className="text-lg font-bold text-yellow-500">{gold} 🪙</div> </div>

<div className="grid grid-cols-1 md:grid-cols-2 gap-4">
    {tasks.map((task) => (
      <Card key={task.id} className="bg-white">
        <CardContent className="p-4">
          <div className="text-2xl">{task.icon}</div>
          <div className="text-xl font-bold">{task.title}</div>
          <div className="text-sm text-gray-600 mb-2">{task.desc}</div>
          <Button onClick={() => completeTask(task.id)} className="bg-orange-400 hover:bg-orange-500 w-full">
            إنهاء المهمة
          </Button>
        </CardContent>
      </Card>
    ))}
  </div>

  <div className="mt-6">
    <Button className="bg-red-500 hover:bg-red-600 w-full text-white font-bold">
      إضافة مهمة جديدة
    </Button>
  </div>
</div>

); };

export default App;

