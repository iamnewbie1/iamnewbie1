- 👋 Hi, I’m @iamnewbie1
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
iamnewbie1/iamnewbie1 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->-- Define the Fly object
Fly = {}
Fly.__index = Fly

function Fly:new(x, y, speedX, speedY)
    local fly = setmetatable({}, Fly)
    fly.x = x
    fly.y = y
    fly.speedX = speedX
    fly.speedY = speedY
    return fly
end

function Fly:update(dt)
    self.x = self.x + self.speedX * dt
    self.y = self.y + self.speedY * dt
end

function Fly:draw()
    print("Fly at position (" .. self.x .. ", " .. self.y .. ") with speed (" .. self.speedX .. ", " .. self.speedY .. ")")
end

function Fly:increaseSpeed(factor)
    self.speedX = self.speedX * factor
    self.speedY = self.speedY * factor
end

function Fly:decreaseSpeed(factor)
    self.speedX = self.speedX / factor
    self.speedY = self.speedY / factor
end

-- Initialize a table to store multiple Fly objects
local flies = {}

-- Add some Fly objects to the table
table.insert(flies, Fly:new(0, 0, 50, 75))
table.insert(flies, Fly:new(10, 20, 30, 60))
table.insert(flies, Fly:new(5, 5, 40, 20))

-- Function to simulate updating and drawing multiple Fly objects over a period of time
function simulateFlies(flies, duration, dt)
    local time = 0
    while time < duration do
        for _, fly in ipairs(flies) do
            fly:update(dt)
            fly:draw()
        end
        time = time + dt
    end
end

-- Function to remove a Fly from the table
function removeFly(flies, index)
    table.remove(flies, index)
end

-- Function to increase the speed of all Fly objects in the table
function increaseSpeedOfAll(flies, factor)
    for _, fly in ipairs(flies) do
        fly:increaseSpeed(factor)
    end
end

-- Function to decrease the speed of all Fly objects in the table
function decreaseSpeedOfAll(flies, factor)
    for _, fly in ipairs(flies) do
        fly:decreaseSpeed(factor)
    end
end

-- Simulate the Fly objects for 5 seconds with each time step being 1 second
print("\nInitial simulation:")
simulateFlies(flies, 5, 1)

-- Increase the speed of all Fly objects by a factor of 2
print("\nIncrease the speed of all Fly objects by a factor of 2:")
increaseSpeedOfAll(flies, 2)
simulateFlies(flies, 1, 1)

-- Decrease the speed of all Fly objects by a factor of 2
print("\nDecrease the speed of all Fly objects by a factor of 2:")
decreaseSpeedOfAll(flies, 2)
simulateFlies(flies, 1, 1)

-- Remove the second Fly from the table
print("\nRemove the second Fly from the table:")
removeFly(flies, 2)
simulateFlies(flies, 1, 1)
