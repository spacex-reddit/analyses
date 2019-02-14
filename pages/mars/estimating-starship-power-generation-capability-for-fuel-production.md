[Original post by /u/CMDR-R0ck3tm4n](https://www.reddit.com/r/spacex/comments/ap7h71/estimating_starship_power_generation_capability/)

---

I thought it would be interesting to calculate just how long it would take for Starship to refuel on Mars, given the effectiveness of solar panels and the energy requirements for fuel production. Before we start, I encourage readers to correct me on any arithmetic errors or other mistakes I may have made :)  tl;dr at the bottom

*I had just finished composing this post when I read the* [*incredible work*](https://www.reddit.com/r/spacex/comments/ap3bz1/estimating_the_mass_of_a_martian_propellant_plant/) *of* u/BlakeMW, who goes into way more detail than me estimating the mass of the whole propellant plant system. Definitely give that post a read as it is far superior to mine!

Assumptions:

* Starship fuel tanks are as described [here](https://en.wikipedia.org/wiki/BFR_(rocket%29#Transport_to_Mars_and_Mars_surface_ship_use))
* whenever a mass is given in "t", I mean metric tons
* no detailed consideration is given to the mass or energy requirements needed to extract/compress CO2 from the atmosphere, mine, heat and purify water, or run other electrical systems on Starship
* it is assumed that a scaled-up Sebatier machine will afford significant mass savings This is complete guesswork for me, so it's likely I've got the mass of the reactor quite wrong
* an arbitrary mass for power conversion and storage equipment is used, as I was not sure how to calculate these.

&#x200B;

**Part 1: How much energy do we need?**

**1a: Sebatier process**

I based this on [this wikipedia article](https://en.wikipedia.org/wiki/Sabatier_reaction) on the process, which claimed that a demonstration machine was able to produce 1kg of methane/oxygen fuel per day while drawing 700w, or roughly 16.8 kWh per kilogram of methalox.

We need to make 960,000kg of the stuff, so multiplying the two together gives us 16.1 million kWh

It is assumed that this very high power requirement will be mitigated after scaling up the machine. Some sources indicate the energy cost of this process could be as low as 9.1 kWh per kg of propellant produced. (check out u/3015's [spreadsheet](https://www.reddit.com/r/spacex/comments/ap7h71/estimating_starship_power_generation_capability/eg6pewp))

Multiply 9.1 kWh/kg by the 960,000kg we need and we get **8,736,000 kWh**

*Splitting water yielding hydrogen we need plus and oxygen produces the exact amount of oxygen to completely burn the methane produced. In fact, we will be left with an excess of oxygen, as the Raptor engine runs fuel-rich, meaning we don't need as much oxygen as we will be producing. Bonus!*

&#x200B;

**1b: Splitting remaining water with electrolysis**

The reactor described above electrolyses waste water to produce extra oxygen and supplement input hydrogen, but only around half of the hydrogen comes from this process, as the reactor assumes a feedstock of hydrogen is brought to mars, rather than produced there from water. Here I will add the energy requirements to supply the rest of the hydrogen

According to [this wikipedia page](https://en.wikipedia.org/wiki/Electrolysis_of_water), a reasonable power requirement for spitting water in this way is 50 kilowatt-hours per kilogram (180 MJ/kg) of hydrogen produced. The Sabatier process requires four hydrogen molecules to be combined with one carbon dioxide molecule to produce 1 methane molecule:

CO2 + 4H2 -> CH4 + 2H20

meaning that we must split 4 water molecules for each methane molecule we produce. To calculate the mass of water we need to split, we find the number of moles of CH4. (I used [this guide](https://www.wikihow.com/Convert-Grams-to-Moles) to remind me of my A-level chemistry)

atomic mass of CH4 = 12 + (4 x 1) = 16

atomic mass of H20 = (2 x 1) + 16 = 18

To find the number of moles we divide the number of grams by the atomic mass of the molecule

240,000,000 / 16 = 15,000,000 moles of CH4

moles of H2 required  = 15,000,000 x 4 = 60,000,000

mass of H2 required = moles x atomic mass = 60,000,000 \* 2 = 120,000,000g or 120,000kg

120,000 \* 50 = 6,000,000 KWh

If we divide this by 2 to account for half the electrolysis already being done by the Sebatier reactor, we are left with **3,000,000 kWh**

also, we can calculate the amount of water we need to mine:

mass of water needed = moles x atomic mass = 30,000,000 x 18 = 540,000,000g or **540t of water**

&#x200B;

**1c: mining, CO2 copression and other energy costs**

I'm not really sure how to calculate the energy needs for compressing and separating CO2 from the atmosphere, mining and purifying water, etc, so perhaps another 1MJ/kg of CH4 for this activity(?)

240,000 \* 1,000000 = 2.4x10^(11) J = **60Kwh total for mining and purification** *(an oversimplification I know, I just don't know how to estimate this)*

&#x200B;

**part 1 summary:**

**total energy requirement** =   **8,736,000 + 3,000,000 = 11,736,000 kWh**

*Amusingly, if we were to buy this amount of energy from the UK national grid at around £0.12 per KWh, it would cost about* *£1,408320 or* US$1,800,000

&#x200B;

**Part 2: how do we generate all this energy?**

Now that we know how much energy we need, we can start to estimate just how feasible it would be to generate this energy.

in order to refuel 1 starship per synodic period (launch window back to earth), we need to spread the above energy requirements over  779.96 earth days *(let's say 780 to make the maths easier)*

number of seconds = 780  \* 24 \*3600 = 67,392,000s

number of joules we need to generate = 11,736,000\* 3,600,000 = 4.22x10^(13)**J** *(3,600000 J in a kWh)*

divide joules by seconds to get power requirements: 4.22x10^(13) / 67,392,000 = **626187W**

&#x200B;

Now we know the power we need, we can work out how many solar cells we need to provide it:

&#x200B;

u/3015 went to great lengths to [calculate](https://www.reddit.com/r/Colonizemars/comments/79k3z4/estimating_the_effectiveness_of_solar_power_at/) the average intensity of sunlight to be 112 W/m^(2) at [Arcadia Platina,](https://en.wikipedia.org/wiki/Arcadia_Planitia) one of SpaceX's [candidate landing sites](https://spacenews.com/spacex-studying-landing-sites-for-mars-missions/), as it is thought there is plenty of underground water there.

If I read the post right, this is an average intensity of sunlight, including night time and accounting for occasional dust storms blocking the light

[This source](https://news.energysage.com/average-solar-panel-size-weight/) suggests a solar panel mass of 2.3 pounds per square foot or, roughly 11.22kg/m^(2) For regular solar panels like you might put on a roof on Earth.

*The general consensus from comments is that ultra-light, flexible solar cells could be rolled out from barrels and fixed to a rigid frame to protect against wind, so I am adjusting the numbers accordingly*

As pointed out by u/BlakeMW in the post linked at the top, multiple companies offer ultra-light, flexible solar cells, with a mass of about 0.2 kg/m^(2). This would need to be added to the mass of a drum or tube for storing the material, as well as the mass of a rigid frame to secure the material to once deployed, to stop it blowing away in the wind. We will take [eRoll](https://flisom.com/wp-content/uploads/2017/08/Datasheet_eRoll_platform.pdf) as our material.

assuming 1.5kg/m**^(2)**  for mounting hardware and rolls/drums for the journey or retraction, ideally mainly using aluminium or carbon fiber. This gives us 1.7kg/m**^(2)**

~~Assuming a 20% collecting efficiency~~  Taking the [quoted efficiency](https://flisom.com/technology/) of 20.4% of our solar panels, we can expect to collect ~~22.4W/m~~**~~^(2)~~** 22.8W/m**^(2)** . Factoring transmission/storage losses of about 10%, that effectively leaves us with 20.52W/m**^(2)**

dividing this into our earlier requirement for 626187W, we get 626187 / 20.52 = 30515m**^(2)** **of panels**

Using our earlier mass of 1.7kg/m**^(2)** , we can say that the solar plant requires **51877kg of panels**

I'm not an electrical engineer, so I don't know how to estimate the mass of power conversion equipment or energy storage, so I'm going to guess at 2t and 4t respectively. Please let me know if these are wildly wrong

To estimate the mass of the sebatier reactor, we can divide the power capability by the power consumption:

9.1kWh per kg of propellant. This is 15% of the power requirements per kg of the original, small reactor. I doubt that the mass savings will be proportional to the power savings, so I'll say that our large reactor is 60% lighter for its output.

240,000kg of propellent over 780 days = 307.7kg/day

307.7 \* 50 = 15,385kg. 40% of this is 6154kg or **6.15t**

&#x200B;

|component|mass(t)|
|:-|:-|
|solar plant|51.9|
|batteries|4|
|mining equipment|5|
|Sebatier reactor|6.15|
|power converters|2|
|total|69.05|

This should easily allow the solar plant, power conversion equipment and chemical equipment to fit within the hold of 1 rocket, with around 30t to spare

&#x200B;

[This sketch shows an area roughly 1\/6th that of the panels we will need, compared to Starship and another familiar spacecraft for good measure](https://i.redd.it/ux4r0x6d8xf21.jpg)

**tl;dr:**

we need to mine and split **540t of water,** and combine it with CO2 to make **240t of methane** and **960t of oxygen**, costing 4.22x10**^(13)****J or 11,736,000 kWh of energy. Making reasonable assumptions about light intensity and solar panel mass, we need deploy 30515m****^(2)** **of solar cells** to collect enough energy to refuel one ship per launch window back to Earth.

&#x200B;

edit1: fixing a broken link

edit2: u/3015 informs me that the Sebatier machine from Zubrin's paper inclides a elecrolysis machine, so I was out by a factor of 2 with regard to electrolysis power requirements. fixed

edit3: redone mass estimates based off some ultra-light panels. Switched to working backwards from wanting to refuel once per synod.

edit4: updated tl;dr

more edits: I ended up redoing this whole post twice due to 2 or 3 big mistakes, so some comments are now outdated as they are talking about my old numbers. Big thanks to everyone for pointing out my errors and suggesting improvements, especially u/3015 :)

&#x200B;
