--Proposiciones
type Proposicion = String

c :: Proposicion -- El sol sale por el oriente
c = "c"

f :: Proposicion -- Los gatos vuelan
f = "f"

t :: Proposicion -- Los perros ladran
t = "t"

y :: Proposicion -> Proposicion -> Proposicion
y p q = "(" ++ p ++ " ∧ " ++ q ++ ")"

o :: Proposicion -> Proposicion -> Proposicion
o p q = "(" ++ p ++ " ∨ " ++ q ++ ")"

implica :: Proposicion -> Proposicion -> Proposicion
implica p q = "(" ++ p ++ " → " ++ q ++ ")"

sii :: Proposicion -> Proposicion -> Proposicion
sii p q = "(" ++ p ++ " - " ++ q ++ ")"

no :: Proposicion -> Proposicion
no p = "¬" ++ p

xor :: Proposicion -> Proposicion -> Proposicion
xor p q = "(" ++ o p q ++ " ∧ " ++ no (y p q) ++ ")"

-- Convinadas
p1 = y c f                            -- El sol sale por el oriente y los gatos vuelan
p2 = o c f                            -- El sol sale por el oriente o los gatos vuelan
p3 = implica c t                      -- Si el sol sale por el oriente, entonces los perros ladran
p4 = sii c t                          -- El sol sale por el oriente si y solo si los perros ladran
p5 = y (no c) (no f)                  -- Ni el sol sale por el oriente ni los gatos vuelan
p6 = xor t c                          -- O bien los perros ladran o bien el sol sale por el oriente

-- Parte 2
m :: Proposicion -- 2 + 2 = 4
m = "m"

r :: Proposicion -- Las rosas tienen espinas
r = "t"

s :: Proposicion -- Un día de la semana es martes
s = "s"

p7 = implica (y r s) m               -- Si las rosas tienen espinas y es martes, entonces 2+2 = 4
p8 = sii r (o (no m) (no s))         -- Las rosas tienen espinas si 2+2 != 4 o no es martes

-- Función principal
main :: IO ()
main = do
    putStrLn "Proposiciones simbolizadas (Parte 1):"
    putStrLn $ "1) " ++ p1
    putStrLn $ "2) " ++ p2
    putStrLn $ "3) " ++ p3
    putStrLn $ "4) " ++ p4
    putStrLn $ "5) " ++ p5
    putStrLn $ "6) " ++ p6

    putStrLn "\nProposiciones simbolizadas (Parte 2):"
    putStrLn $ "7) " ++ p7
    putStrLn $ "8) " ++ p8
