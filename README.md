using System;

class VirtualPet
{
    public string type;
    public string name;
    public int hunger;
    public int happiness;
    public int health;
    public VirtualPet(string petType, string petName)
    {
        type = petType;
        name = petName;
        hunger = 5;
        happiness = 5;
        health = 5;
        }
public void Feed()
{
    Console.WriteLine($"You feed {name}.");
    hunger = Math.Max(1, hunger - 2);
    happiness = Math.Min(10, happiness + 1);
    health = Math.Min(10, health + 1);
}
public void Play()
{
    Console.WriteLine($"You play with {name}.");
    hunger = Math.Min(10, hunger + 2);
    happiness = Math.Min(10, happiness + 3);
    health = Math.Max(1, health - 1);

    if (hunger >= 8)
    {
        Console.WriteLine($"{name} is too hungry to play!");
    }
}
public void Rest()
{
    Console.WriteLine($"You let {name} rest.");
    health = Math.Min(10, health + 2);
    happiness = Math.Max(1, happiness - 1);
}

public void DisplayStatus()
{
    Console.WriteLine($"{type} {name}'s Status:");
    Console.WriteLine($"Hunger: {hunger}/10, Happiness: {happiness}/10, Health: {health}/10");
}
public void CheckStatus()
{
    if (hunger <= 2)
    {
            Console.WriteLine($"{name} is starving! Please feed {name}.");
    }
    else if (happiness <= 2)
    {
        Console.WriteLine($"{name} is very sad! Play with {name} to cheer it up.");
    }
    else if (health <= 2)
    {
        Console.WriteLine($"{name}'s health is low! Give {name} some rest.");
    }
}

public void TimePasses()
{
    Console.WriteLine("Time passes...");
            hunger = Math.Min(10, hunger + 1);
        happiness = Math.Max(1, happiness - 1);
    }
}
class Program
{
    static void Main()
    {
        Console.WriteLine("Welcome to Virtual Pet Simulator!");

        Console.Write("Enter the type of pet (e.g., cat, dog, rabbit): ");
        string petType = Console.ReadLine();

        Console.Write("Enter a name for your pet: ");
        string petName = Console.ReadLine();
        VirtualPet pet = new VirtualPet(petType, petName);

        Console.WriteLine($"You adopted a {pet.type} named {pet.name}!");
while (true)
{
    Console.WriteLine("\nChoose an action:");
    Console.WriteLine("1. Feed the pet");
    Console.WriteLine("2. Play with the pet");
    Console.WriteLine("3. Let the pet rest");
    Console.WriteLine("4. Display pet status");
    Console.WriteLine("5. Exit");

    int choice;
    if (int.TryParse(Console.ReadLine(), out choice))
    {
        switch (choice)
        {
            case 1:
                pet.Feed();
                break;
            case 2:
                                    pet.Play();
                        break;
                    case 3:
                        pet.Rest();
                        break;
                    case 4:
                        pet.DisplayStatus();
                        pet.CheckStatus();
                        break;
                    case 5:
                        Console.WriteLine("Goodbye!");
                        return;
                    default:
                        Console.WriteLine("Invalid choice. Try again.");
                        break;
                }

                pet.TimePasses(); // Simulate the passage of time after each action
            }
            else
            {
                Console.WriteLine("Invalid input. Please enter a number.");
            }
        }
    }
}
