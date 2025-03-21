import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";

const subjects = [
  { name: "Structural Engineering", files: ["Concrete Design.pdf", "Steel Structures.pdf"] },
  { name: "Geotechnical Engineering", files: ["Soil Mechanics.pdf", "Foundation Engineering.pdf"] },
  { name: "Transportation Engineering", files: ["Highway Design.pdf", "Traffic Analysis.pdf"] },
  { name: "Hydraulics & Hydrology", files: ["Fluid Mechanics.pdf", "Water Resource Management.pdf"] },
  { name: "Construction Management", files: ["Project Scheduling.pdf", "Cost Estimation.pdf"] },
];

export default function CivilTech() {
  const [search, setSearch] = useState("");
  
  return (
    <div className="p-6">
      <h1 className="text-3xl font-bold mb-4">Civil Tech - Engineering Review</h1>
      <Input 
        placeholder="Search subjects..." 
        value={search} 
        onChange={(e) => setSearch(e.target.value)} 
        className="mb-4"
      />
      <Tabs defaultValue="Structural Engineering">
        <TabsList className="mb-4 grid grid-cols-2 gap-2 overflow-x-auto">
          {subjects.map((subject) => (
            <TabsTrigger key={subject.name} value={subject.name}>
              {subject.name}
            </TabsTrigger>
          ))}
        </TabsList>
        {subjects.map((subject) => (
          <TabsContent key={subject.name} value={subject.name}>
            <Card className="max-h-60 overflow-y-auto">
              <CardContent>
                <h2 className="text-xl font-semibold mb-2">{subject.name}</h2>
                <ul>
                  {subject.files.map((file) => (
                    <li key={file} className="mb-1">
                      <Button variant="link" className="text-blue-600">{file}</Button>
                    </li>
                  ))}
                </ul>
              </CardContent>
            </Card>
          </TabsContent>
        ))}
      </Tabs>
    </div>
  );
}
