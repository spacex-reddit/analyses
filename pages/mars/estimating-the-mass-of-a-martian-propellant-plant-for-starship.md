[Original post by /u/BlakeMW](https://www.reddit.com/r/spacex/comments/ap3bz1/estimating_the_mass_of_a_martian_propellant_plant/)

---

# TL;DR

Fair enough... this is a really long post. And I still feel like I don't go into nearly enough detail.

| Category | Mass |
|--------------------------|------|
| Solar Power Generation | 25 t |
| Electrolysis | 4 t |
| Day-Night Energy Storage | 7 t |
| Water Extraction | 4 t |
| Earthmoving | 8 t |
| Backup Power Generation | 2 t |
| Cooling | 7 t |
| Atmospheric Extraction | 3 t |
| Sabatier Reactor | 1 t |
| Cryocoolers | 3 t |
| Miscellaneous | 10 t |
|  |  |
| **Total** | 74 t |

# Assumptions and methodology

I am working on the assumption of a 1 MW solar-powered propellant plant located at equatorial latitudes (0-30N) capable of refueling one Starship per Earth-Mars synodic period, I'm curious what it might mass in at and especially the ratio of propellant plant Starships to Starships refueled per synod.

My methodology is to divide the plant into broad categories, doing an analysis to get a broad idea of requirements then finding commercial products that are a close match (provided they include the weight value), ideally I can find something which is aerospace grade. I'll also reference studies from NASA and such: if I have a reluctance to reference NASA studies it's firstly because some are really old and secondly because SpaceX would have to take a COTS approach to keep costs down, of course when each Starship sent to Mars probably costs ~$250 mil it's reasonable to spend around $2million/t on payload : but that's nothing like the $2billion/t for a Curiosity rover. Also, having 100 t to play with is amazing.

As a note, if ever I link to a particular product, **that in no way implies that I think that particular product would be suitable for use on Mars** it is just to get a ballpark figure, even very good matches would need significant customization. If the thing linked is consumer/industrial grade rather than aerospace it could be available in a *much* lighter package. Replacement parts will be needed and I often significantly pad numbers for this reason.

Even if I only link to one example I usually try to find several other examples as a sanity check even if I don't bother linking to them.

Scaling is super important for some things. Solar PV masses the same per watt whether it's 10 W or 10 GW and this is true of nearly all solid state electronics, but thermo-mechanical stuff often scales up extremely favorably: I'm mentioning this here because extrapolation from a system which generates 1 kg/day to a system which generates 1000 kg/day may be close to meaningless. I generally try to find hardware on the same order of magnitude unless I'm confident the mass scaling is linear.

Naturally my methodology will not produce a perfect result especially since we have almost no details of SpaceX's plans, it's like if they declare "we're going to land at 45N and use tilted single-axis tracking solar panels" that would shake things up. My goal is merely to produce a plausible number, as in "it could plausibly be achieved with about this much mass using basically commercial products".

Generous margins are included. For example a Starship should be able to return to Earth with only 70-80% full tanks, but I assume full tanks. Power production and electrolysis capacity are oversized by about 50%.

# Solar Power Generation

I am assuming 10 MW nameplate capacity to get a daily average of 1.5 MW before atmospheric and accumulated dust. Total power requirements to refuel 1 Starship per synod is probably somewhere around 1 MW for 600 days.

A company Flisom promotes two interesting products: [eRoll](https://flisom.com/wp-content/uploads/2017/08/Datasheet_eRoll_platform.pdf) at 0.2 kg/m^2 and 100 W/m^2. These arrays at the 10 MW nameplate capacity would mass in at 20 t. These are still 3x as heavy as the lightest possible arrays allowing for durable protective coatings.

The other is [eFilm](https://flisom.com/wp-content/uploads/2017/08/Datasheet_ultra-light-CIGS-eFilm-solar-cell-material.pdf) at 0.06 kg/m^2 and specific power up to 2 kW/kg, these would mass in at just 5 t. I believe the eFilm would be too light and flimsy to be suitable in the martian environment for some perspective it's basically the same weight as printer paper. So I'm noting it here but not assuming it would be used, though it might be useful as part of a sandwich with other specialized layers, or for use with ISRU "dumb" mass.

Furthermore there is mounting hardware to consider. It might involve grading the surface then just staking the solar blankets to the ground so high speed winds can't shift them. There are better options in the long run but roll out solar blankets with durable coatings seem plausible.

Wiring and such are also needed. The solar strings would probably run at fairly high voltage so the cabling doesn't need to be that heavy but the equipment for power conditioning and conversion (i.e. charge controllers, DC-DC converters) might be significant. This is hard to estimate without a full design of the power grid, a majority of the power goes to the electrolysis cells and the more direct a connection is used the less mass is needed for power conversion and regulation. We do at least know that the grid would be DC as Elon Musk has [stated as much](https://twitter.com/elonmusk/status/840772319526113280?s=21) and it totally makes sense. This means that inverters and rectifiers are not needed except maybe in a few places.

Searching for "DC-DC converter for electric aircraft" yielded results like [Compact and Lightweight Aviation Power Electronics](https://www.iisb.fraunhofer.de/content/dam/iisb2014/en/Documents/Research-Areas/vehicle_electronics/Publications/Aircraft_Electronics/FraunhoferIISB_Brochure_Compact%20%26%20Lightweight%20Aviation%20Power%20Electronics.pdf) at power density of 62 kW/kg at which rate DC conversion for 4 MW would weigh in at 64 kg (refer to cooling though for additional mass requirements associated with power conversion)

* Solar panel mass: 20 t
* Mounting, power conversion etc: 5 t (?)

# Electrolysis Stacks

Another major component will inevitably be electrolysis stacks.  The latest numbers we have to completely fill a Starship are 240 t methane and 860 t oxygen:

* 240 t of methane produced via Sabatier reaction requires 120 t of hydrogen which requires the electrolysis of 1080 t of water and average power consumption of 406 kW assuming 50 kWh per kg of hydrogen
* 860 t of oxygen requires the electrolysis of only 970 t of water, hence a 100 t surplus of oxygen will be created: enough to supply 130 humans for 26 months!

I am assuming that electrolysis will be performed while the sun shines as I can't conceive of a way that energy storage for night-time operation could come even close in mass to day-only electrolysis. This means it needs to be sized to the peak power rather than the average. Peak generation would be around 4 MW and not all of that has to go to electrolysis but a majority does, also electrolysis would probably have the lowest priority for morning and evening solar power with priority going to things like cryocoolers. Hence something like 2-3 MW of electrolysis capacity.

This might actually be surprisingly light. For example [this pdf from 2014](https://www.energy.gov/sites/prod/files/2014/03/f12/webinarslides052311_pemelectrolysis_hamdan.pdf) claims 1 kW/kg for old technology, predicting 2.4 kW/kg in the times we live in now. That would be roughly 1-2 t. Also water electrolysis is largely symmetrical with hydrogen fuel cells, and see below for fuel cell masses.

[This product from Hydrogenics](https://www.hydrogenics.com/wp-content/uploads/HyLYZER_600_3MW.pdf) is a 3 MW electrolysis stack with dimensions of 550 mm x 880 mm x 1150 mm, it doesn't give a weight but that volume is insanely small and supports the idea that the electrolysis stack could be just 2 t or so.

It might also be necessary to provide hydrogen storage as I am fond of the idea of being able to run the sabatier reactor at night as it is exothermic and it would allow the reactor to be continually operated, and radiators to be utilized at night as well as during the day.

The cells would need to produce about 260 kg/day of hydrogen, if it were desired to have 16 hours worth of storage for night that would require a ~1 t hydrogen tank (using a 1:8 ratio of compressed hydrogen to tank). They would also produce 2340 kg/day of oxygen which might all be immediately cryocooled or a portion might be stored to be cooled at night.

* Electrolysis stack: 2 t
* Hydrogen storage: 1 t
* Oxygen storage: 1 t

# Day-Night Energy Storage

It is often assumed that Lithium-ion batteries will be used. This might not be a fair assumption, hydrogen fuel cells seem to offer a much better power density and if the power generation is lightweight enough and the electrolysis mass-efficient enough, it seems to be logical route for power storage. Yeah I know Elon Musk called them Fool Cells but was that in the context of vehicles on Earth or a base on Mars? A "hydrogen economy" is not optional on Mars, though I do think vehicles would use batteries because having to fill separate hydrogen and oxygen tanks and potentially unload a water tank would suck.

There are two things to consider, the power required at night and the energy storage. Power might be 100 kW, which is a bit of an ass-pull but seems fair (in particular see cryocooling), and it would be needed for about 14 hours when the sun is not high in the sky but I'll use 16 hours for a bit of extra margin.

* Power: 100 kW
* Storage: 1.6 MWh

This minimum of storage could be provided with 8 Tesla Power Packs, which would provide an ample 400 kW of power output and weigh 13 t (altough it might be a bit less if optimized for mass, the battery modules themselves should only weigh about 8 t with the rest of the mass being things like rectifiers and cooling systems, some of that is needed on Mars too so I'll call it 10 t). Batteries are probably not the best option, though batteries are also good for power conditioning, helping to maintain a stable voltage even when supply and load are mismatched or to handle spikes (for example when a vehicle plugs in to recharge), for this reason alone it would make sense to have at least 200 kW of battery power output.

I found [these fuel cells](https://www.intelligent-energy.com/uploads/product_docs/AC64_LW_datasheet.pdf) that are rated at 1800 W @ 975 g and are aerospace grade, often I couldn't find weights for aerospace grade stuff, in this case I could as they are used in drones.

To get the desired power of 100 kW would require 54 kg of aerospace grade fuel cells. Hydrogen theoretically provides about 25 kWh/kg so storage for 64 kg of hydrogen would be required, pressure vessels mass at least 8x the mass of the hydrogen so I'll call it 640 kg. 9 kg of oxygen is required per 1 kg of hydrogen so storage for 576 kg of oxygen is required. I figured the most lightweight oxygen tanks in existence are probably those used [by Mountaineers](http://summitoxygen.com/summit-standard-system/) and those can contain 1.6 kg of oxygen in a 2.2 kg cylinder, I believe that the mass of a pressure vessel is linear with respect to the mass of the pressurized contents and so the 576 kg of oxygen would require a 800 kg tank.

Ultimately the night-time power using fuel cells seems to mass in at about 2 t and batteries about 10 t, the round trip efficiency for fuel cells is a little lower, it might be something like 90% for batteries and 60% for fuel cells but the lower efficiency only increases the solar power requirements by about 3%. Nevertheless, I think a combination of batteries and fuel cells would be a reasonable solution, with fuel cells providing the bulk of the storage. At higher latitudes (> 45N) batteries may become favorable due to low solar efficiency in winter.

* Tesla Powerpacks (DC): 5t (200 kW, 800 kWh)
* Fuel cells: 100kg (100 kW)
* Hydrogen Storage: 640kg (1600 kWh)
* Oxygen Storage: 800kg
* Total: 7 t (for a total of about 24 hours of storage)

# Water Extraction

The two basic proposed strategies for extracting water which would be most effective are digging up chunks of icey regolith and baking it, or a Rod well (actually multiple, over time) - I'm not going to consider atmospheric extraction. I like to assume ice will be confirmed by a previous robotic mission.

Water extraction is central to the entire scheme, as important as power generation. About 600 t of water would be required for producing the propellant to refuel one Starship but I think it's safe to double that to 1200 t to account for human needs and wasteful use of water. This would require extraction at a rate of 2 t/day.

This works out to 1.3 kg/minute or 22 g/s  (that is, the required extraction rate is so low it would take a couple of minutes to fill a 3 L softdrink bottle). Melting this much ice (from -50C to 10C) would require 10 kW of heat input (1% of the total propellant plant requirements): waste heat could be used for this. Maintaining the Rod well (that is, maintaining the pool of liquid in the void) requires more heat due to losses into the surrounding ice [this NASA study](https://www.nasa.gov/sites/default/files/atoms/files/mars_ice_drilling_assessment_v6_for_public_release.pdf) indicates something in the ballpark of 50 kW. Long, insulated, electrically heatable pipes would probably be used to circulate water between the propellant plant and the Rod well, serving to deliver waste heat to the well and water to the propellant plant. Some water is needed to start up a Rod well, this might be extracted with the assistance of an electrical heating element that is lowered into the ice or perhaps the prior robotic mission.

The water would probably be purified by vaporization with the vapor being re-condensed by heat exchange with the incoming water if needed. This vaporization would require roughly 55 kW but waste heat can be easily used for this as the water/steam is mostly needed where the waste heat is generated.

An ice-chunk melting setup could be embarrassingly simple but feeding it ice on an ongoing basis seems to be much higher-effort than drilling a well. Contingent of course, on underground ice being confirmed.

Some kind of air drilling (there are several) could be used which involves a pneumatic hammer/rotary drill head powered by compressed air which is also used to cool the drill and flush cuttings out of the borehole, the substrate being drilled into should basically be dry which simplifies things vs earth where wet layers can greatly complicate air drilling.

Compressed air could be delivered to the drilling rig in a pressure vessel on a trailer. The equipment to compress air is needed anyway but it might be hard to deploy it in the field. Alternatively there might be field compressors for cleaning solar panels with compressed air.

There are innumerable small rigs in the range of masses from [150 kg](https://www.alibaba.com/product-detail/hard-rock-drilling-machine-compressed-air_60768524128.html?spm=a2700.7724857.normalList.2.6bc0288amS7SOv&s=p)-500kg which would likely provide ample diameter and depth (50-100 m). In fact it doesn't seem that water extraction would be a major fraction of the mass, even small man-portable rigs seem capable enough, though it would probably be desirable to robotize the rig to some extent.

The equipment including borehole casings could also be made using very lightweight materials, often on Earth PVC is used which is pretty light (a few kg/m).

* 2x Mini Drilling Rig: 2 t
* Pipes etc: 2 t


# Earthworking

I have referenced grading and rolling as a way to prepare surfaces for many hectares of roll out solar blankets.

To me it seems logical to bring several electric mini-excavators, something like [this from Volvo](https://www.volvoce.com/global/en/news-and-events/news-and-press-releases/volvo-ce-unveils-100-percent-electric-compact-excavator-prototype/) with the cab being replaced by an autonomous control system (if we must it can include a command chair but the surface of Mars isn't a nice working environment) and it might be a good idea to have a bigger battery to help run attachments. Ideally you want these little excavators to be able to spend hundreds of days preparing surfaces and performing other tasks. These excavators could also tow stuff (i.e. unroll solar blankets) or use attachments other than a bucket and blade, for example a blower using compressed air to clean solar panels. These mini-excavators seem to generally mass in at around 1-2 t depending how "mini" you want to go. Also there are [wheeled skid-steer loaders](https://bobcatofaustralia.com.au/bobcat-model/51/Bobcat-S70) in a similiar weight class.

There are those that may object that these excavators are too small, however the challenge of building a base on Mars is not that it's a huge construction project - actually it's a relatively puny job relative to constructions projects on Earth and there's a lot of time to complete it - the challenge is it has to be done *on Mars*. It would be harder to get larger/heavier vehicles out of the cargo hold and there would be less redundancy than with a bunch of small vehicles.

* 3x Mini-excavators: 6 t
* Attachments etc: 2 t

# Backup Generation

It can be assumed that some percentage of solar power remains available during severe dust storms, 5% might be reasonable. Propellant production would be shut down to conserve power for essential functions. Note that unlike most of this analysis, the backup power here is more to provide redundancy for the crewed based, than for the sake of the propellant plant itself, however it is closely tied to the propellant plant as energy storage in hydrocarbons presents one of the only viable medium-term energy storage options.

I will assume that 50 kW is needed, 100 kW is desirable (i.e. to continue to power workshops and labs so the humans haven't just come to Mars to sit on their hands) and total generation including solar should be 200 kW for redundancy.

Probably no power generation is needed during the day thanks to solar power, but there might not be enough solar to both provide daytime needs and to recharge the batteries. In less severe dust storms there would still be enough solar power to run all the essentials and having to resort to non-solar might be something that only happens for a few weeks once a decade : this deserves closer examination but we do know that solar-powered Opportunity Rover survived nearly 15 years before there was a dust storm severe enough to end its life.

During a dust storm battery powered vehicles would be kept plugged into the grid both to save the power the vehicle would otherwise be using and to contribute their battery capacity to the grid, eliminating the reliance on hydrogen fuel cells when little solar power is available for electrolysis.

For these severe storms there are four main options I can see:

* Nuclear Power such as 10 kW kilopower units
* Steam reforming of methane to hydrogen for use in the hydrogen fuel cells (note: most methane fuel cells are really just hydrogen fuel cells with additional equipment that performs steam reforming)
* ICE generator probably a methalox turbine <- this one is probably best!
* Wind turbines

I do not think that Nuclear Power is a credible option *at all* due to it being a quagmire of delays and bureaucracy and there being much easier options that suffice.

If the cryocoolers are shut off to save power the methalox will start boiling off, if it boils off at a rate of 0.1% per day that would provide 240 kg of methane per day (and oxygen too), which could be used to generate about 55 kW of electricity on a continual basis, this seems like a bit of a "use it or lose it" situation. As a note the plant produces around 400 kg of methane a day, so 1 "clear skies" day of methane production would provide 1.6 days of emergency power, and this is a horrendous round-trip efficiency but its probably going to be used less than 1% of the time.

A 60 kW generator tends to mass in at about 1 t (example [850 kg diesel](https://www.powerelectrics.com/docs/default-source/sales-products-pdf-spec-sheets/p65-5(4pp)gb(0514).pdf?sfvrsn=2), [760 kg turbine](https://www.capstoneturbine.com/products/c65). An ICE generator whether diesel or turbine might need special cooling strategies due to the high methalox flame temperature, this would probably involve using compressed martian atmosphere as diluent and/or film cooling of turbine blades, the propellant plant would provide compressed atmosphere anyway. The best aerospace grade generators would be significantly lighter than these examples, possibly around 200 kg for a 60 kW generator, altough a heat exchanger for combined heat and power would be desirable.

Overall the fuel cells and generators seem quite comparable in terms of mass, being a few hundred kg. In the future methane fuel cells will likely be a superior option but right now they still have most the downsides of a gas turbine (i.e. operating at high temperatures) and it would seem desirable to use equipment designed for reliable standby/emergency generation.

During dust storms on Mars, wind turbines ought to be able to produce a significant amount of power, though turbines capable of doing so would produce basically no power during non-storms. I found [this lightweight wind turbine](https://www.leadingedgepower.com/documents/LE-600-wind-turbine-datasheet-web-Aug2018.pdf) a bit smaller than I'd like but it has a detailed datasheet, a 30 m/s wind on Mars would be equivalent to a 8 m/s wind on Earth and this turbine would thus produce ~160 watts and as it weighs 20 kg the specific power is 8 W/kg, that is much worse than the 60-200 W/kg for an ICE generator and it seems unlikely that even de-robustifaction could make it competitive. Still, plausibly 50 kW of backup power could be provided by 6 t of Wind Turbines, it's not so terrible as to be beyond consideration, in fact it feels worthwhile bringing a few turbines just to see how well they perform or using them to power remote monitoring stations during dust storms.

It's worth noting that every backup option except wind produces a substantial amount of usable thermal energy (about equal to electrical), normally thermal energy is kind of a nuisance, but with everything shut down it will be useful for keeping the plant warm: it's actually another strike against wind.

* 2 x 60 kW gas turbines: 1 t
* Fuel Cells + Steam reforming: Free/trivial, the required stuff is already present or the engineers can improvise it.
* 10 kW of wind turbines: 1 t

# Cooling

Of the 1 MW electrical generation about 20% of that ends up in propellant and the other 800 kW mostly ends up as waste heat, under Water Extraction I established that heat demands for water extraction is about 60 kW and that provides a small source of high-grade cooling, also heat leaking out of the Starship/building also provides a source of cooling (maybe 100 kW). Not all of the surplus waste heat needs to be discarded as some of it can be used to keep the equipment warm, however I think that most equipment should be well insulated so that if it has to be powered down due to lack of electricity it does not rapidly cool down: thermal cycling reduces the lifespan of equipment, freezing can be damaging. Also components that run at wildly different temperatures have to be isolated from each other, so it is fair to assume that most heat is only getting out intentionally, when the coolant pumps are running.

Taking the earlier example of the 3 MW electrolysis stack, if you put 3 MW into a box less than 1 m^3 at 80% efficiency then that box is going to get very, very hot due to the ~ 0.6 MW of waste heat that needs to be discarded, these stacks do operate at fairly high temperatures (120C) and that improves their efficiency by letting them utilize some of their own waste heat for splitting water, but nevertheless the temperature must be maintained at safe levels (note that the hot hydrogen and oxygen carries away some of the heat: nevertheless, we need to cool that hydrogen and oxygen so that heat has to be discarded). Other things also end up producing significant heat, for example 95% efficient power conversion on 4 MW is still 200 kW of waste heat. It's fun to compare these numbers with household heaters - a 2 kW heater would keep a room nice and warm while an industrial space heater might be rated at 10 kW. Just the waste heat from high-efficiency power conversion could easily be enough to overheat a propellant plant integrated into a Starship cargo bay.

The amount of radiator surface required depends on the temperature the equipment operates at which sets the minimum radiator temperature, the Stefan–Boltzmann law can be used to calculate the power radiated which is proportional to temperature in kelvin to the fourth power. For example a blackbody radiator at 200 C would discard 2.8 kW/m^2, at 600 C it would discard 32 kW/m^2. Particularly when you have high grade heat you can get a bit more work out of it (in accordance with Carnot Efficiency), but in the process you increase the amount of radiator surface required. For example say you have 100 kW of 600 C heat: you could discard that directly into ~3 m^2 of 600 C radiator. Or you could put it through stirling engines to generate ~40 kW of electricity, and then discard 60 kW of heat into 370 m^2 of 30 C radiators. There is no free lunch when it comes to utilizing waste heat as the lower you go the more radiator surface is required until you finally reach a point where more power is required to run the coolant pumps than can be derived from the heat: it becomes uneconomical long before this.
 
It's very much favorable if equipment operates at higher temperatures, that really makes the cooling easier, so if your power conversion equipment is okay operating at 200 C that's a big help.

Cooling requirements estimate: 3 MW goes into electrolysis units at 80% efficiency generating up to 600 kWt during the day time. The other 1 MW also mostly ends up as heat in compressors and such for another 600 kWt making the peak heat disposal 1200 kWt at midday. I'll assume the heat is discarded at 120 C. For this the required radiator surface would be around 1000 m^2. How big is 1000m^2? It happens to be about the surface area of a Starship, so if a Starship were a perfect blackbody - it's not, stainless steel has very low emissivity - it would be able to maintain a thermal equilibrium at about 120 C. In that sense discarding heat by radiation isn't that ineffective, but the comparison with Starship area is just a fun fact: the actual form the radiators would take would probably be rollout radiator blankets or bi-facial upright panels facing north-south to reduce sunlight load, the upright panels by doubling the available radiator area and getting out of direct sun would be much more efficient especially during the day and would probably be the best approach despite the increased difficulty of deployment (for example radiator fences, along with having to be erect, can't be spaced too close together, that means they have to be quite long, but a radiator fence could potentially be deployed up a slope so coolant flows back to the plant under gravity).

I had trouble finding numbers for commercial lightweight radiators but I could find numerous [studies from nasa](https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/19980236936.pdf) and such and it seems fair that a radiator might mass in at 5 kg/m^2 without needing to assume anything crazy (this is still 60x heavier than paper, and the theoretically lightest radiators actually would be paper thin, exploiting highly directional conduction in carbon fiber and the like). This is an area where there is a heap of scope for mass reduction with the question being if it's really worth it vs say aluminium radiators, ultimately I'll go with 4 kg/m^2.
               
A note about convective cooling: Convective coolers will work on Mars, unlike in a vacuum. They have the potential to be much more compact but would be inferior in terms of both mass and energy efficiency relative to radiative solutions, because extremely large volumes of air would need to be forced through the cooler: using 20 g/m^3 for atmospheric density, 0.791 kJ/(kg K) for specific heat and assuming the air can be heated by 150 K, disposing of 1 MW of heat would require pumping 420 m^3 per second which would require some combination of extremely large and extremely fast spinning fan. I'm not going to try and estimate the mass and energy requirements of this cooler but I'm pretty sure it's worse than the radiator arrays (I haven't found any study that favors convective cooling), and it can't be sealed against dust.

The precise details of the equipment such as operating temperatures have the potential to make a significant difference to these numbers.

* 1000 m^2 of 120 C radiator: 5 t (?)
* Plumbing, heat exchangers etc: 2 t (?)

# Atmospheric extraction

Along with water the other important ingredient for rocket propellant is carbon dioxide. This requires that the martian atmosphere be sucked in, filtered, compressed, cooled, compressed some more and so on until the CO₂ gas condenses, any water ice can be scooped out and the nitrogen, argon, carbon monoxide and oxygen gases drawn off. This process ultimately produces a lot of CO₂, a little nitrogen and argon, and trifling amounts of water, carbon monoxide and oxygen.

The 240 t of methane would require require a total of 660 t of CO₂, this is about 1 t/day and if we assume this part of the plant operates for 10 hours a day using direct solar power that would require ~32 g/s of atmosphere be processed, this is about 1.5 m^3/s of air. If a pump had an inlet with an area of 0.1 m^2 then that would create a 15 m/s wind. This is a useful ballpark figure to know, if the mass flow rate required a supersonic wind into a 1 m^2 inlet we would have problems. At this flow rate, it seems conceivable this equipment could fit within a 1 m^3 cube and be kept in a Starship cargo bay, simply opening a vent to let air in.

One interesting bit of reading is the [MARRS direction extraction concept](http://www.niac.usra.edu/files/studies/final_report/483England.pdf) which called for the processing of very large amounts of atmosphere on the order of 10 t/hour as the goal is to extract oxygen (at 0.096 wt% of the atmospheric gasses), that's around a hundred times the rate needed here. Their system mass estimate was around 13 t including a nuclear power system (5 t). While I'm uncertain of the mass scaling, if we assume that scaling it down 10-fold results in a 4-fold mass reduction it'd come to 0.8 t.

Some tanks would also be required, for liquid CO₂, nitrogen and argon. Liquid CO₂ is easier to store than oxygen and less of it is produced each day, and the nitrogen and argon would probably be delivered to the crew habitat so 1 t of tankage is probably ample.

This section does deserve more examination, but much as with electrolysis I believe this process would be much more energy intensive than mass intensive and even more extremely amenable to mass-optimizations.

* Atmospheric Extraction: 2 t
* Tanks: 1 t

# Sabatier Reactor

The reactor would need to generate ~400 kg of methane per day and needs to take in hydrogen and carbon dioxide at elevated pressures, fortunately electrolysis produces high pressure hydrogen and the carbon dioxide will also be at high pressure after being re-expanded from liquid, so getting the inputs into the reactor is pretty much opening some valves. 

The reactor outputs methane, water vapor and potentially unreacted carbon dioxide or hydrogen. The methane has to be separated out and purified as required, the water should be separated out and recovered and the other gases cycled back in for another pass through the reactor.

Mass estimates are tough, there are a number of proposals from NASA and such for sabatier reactors however these are for very small scale (1 kg/day) and operate at low pressures (~1 atm), scaling the numbers up to the 400 kg/day is unlikely to produce valid numbers due to scaling factors. As such I will use Zubrin's estimate from [this study](https://pdfs.semanticscholar.org/9159/213d6ad79bd800d07525bc37463588742662.pdf)(page 15) for a 500 kg/day Sabatier+RWGS reactor, of 691 kg - in my analysis the reactor runs day and night and I treat the chemical synthesis separately so the adjusted mass would be around 250 kg.

Also note: A reverse-water-gas-shift reactor is not essential when water mining is assumed. If one is desired it'd be about 350 kg.

Ultimately I'm just going to call it 1 t.

* Sabatier Reactor: 1 t

# Cyrocoolers

Last but not least are the coolers responsible for taking the hot methane from the sabatier reactors and hot oxygen from the electroylsis stacks and chilling it to around -160/-180 C (pressure might be manipulated to prevent the methane freezing). The coolers are also responsible for preventing the escape of boil-off, either by deep-chilling the propellant or through boil-off re-liquefaction. In total around 1800 kg of methane and oxygen would need to be liquefied per day and perhaps about half that in boil-off. Also a considerable mass of CO₂ needs to be liquefied, however the CO₂ needs to be heated before entering the sabatier reactor and could exchange heat with methane ready to enter the coolers.

Due to wariness around scaling I wanted to find something with comparable performance to the requirements [this liquid air generator](https://www.stirlingcryogenics.eu/files/__documents/1/StirLAIR-4TechnicalSpecification.pdf) can liquify ~1000 kg of air per day and weighs in at 4 t - it includes some stuff not strictly needed. Also it's not aerospace grade, I didn't have much luck finding cryocoolers for use in aircraft or space which weren't in the tens of watts power range rather than the kilowatts we are interested in here. I'm sure large mass savings could be had if the system is optimized for mass.

Reasonably high grade cold is available on Mars, on Earth heat often has to be discarded at ~25 C, on Mars even at the equator the sky is extremely cold at night, possibly as low as -130 C. During the day there is significant heat load from direct and indirect sunlight and the atmosphere can be warmer but convective heat transfer is very low and heat transfer is still dominated by radiation, if the panels are not exposed to direct sun they would still be reasonably cold even during the day. The radiator arrays would have to be sizable, but as previously established under cooling, they are *big* but not that *heavy*. The low temperature of the environment would significantly improve the performance of the cryocoolers (as per Carnot Efficiency) probably by something like 30%.

The Cryocoolers are one of the major components I'm least certain about, it's not even clear if it's better to run them only during the day, or to run them day and night, requiring less mass and taking advantage of cold night time temperatures to better utilize the radiators, or to deep-chill during the day to save power at night. My intuition is it makes sense to run them 24.6/7 with power storage being less massive than more coolers, consumption seems to be in the ballpark of 60 kW and so the cryocoolers represent a significant chunk of the nightly power usage.

It should go without saying, that the methalox will initially be stored in Starship propellant tanks. Extra insulation might be useful, maybe wrapping a Starship in an MLI cosy (this deserves further examination).

Ultimately munging these factors together and some details from the previously linked paper from Zubrin I conclude 3 t might be a reasonable mass.

* Cryocoolers: 3 t (?)

# Miscellaneous

Then there is all that other stuff like cables, mounting brackets, access ways, protective packaging, crane/lift, trailers/sleds, insulation, MLI  tents to protect equipment during severe dust storms, insulated pipes to pump methalox between Starships so on.

It's not clear exactly how much of this stuff will be needed. Clearly, solar panels, wind turbines, radiators, vehicles and water extraction equipment have to be deployed outside. Other than that the propellant plant could be integrated into the cargo bay of the Starship if SpaceX is fully committed to not returning that Starship (which seems to be the case for early Starships), or it could be almost entirely unpacked and deployed in surface buildings to consolidate the propellant plant equipment from multiple ships into a single complex. Surface buildings, for instance, could require a fair amount of extra mass.

* Miscellaneous: 10 t (?)

# Conclusion

The final number I came up with is 74 t. Working on the assumption that Starship can land 100 t on Mars that would easily fit within the payload capacity with some leftover for more redundancy.

This would mean that two Starships could land, each with a complete propellant plant which in an ideal world can fully refuel a single Starship per synod, that means that if everything goes well two Starships could be returned around 26 months later.

Coming into this exercise I assumed the propellant plant equipment would be much heavier, maybe 200 t. Many components turned out to be much lighter than I expected: like the solar panels, water extraction, electrolyzers and power storage, and whenever I looked into aerospace stuff I was impressed by how crazy lightweight it can be. 

One surprising conclusion: if a Starship can land 150 t as per original BFS specs, each Starship could carry enough hardware to refuel 2 Starships per synod.

Furthermore, the equipment for adding 1 MW of capacity to the existing propellant plant is considerably less than 76 t, probably closer to 50 t (i.e. stuff like solar panels which you plain and simply need more of), thus each Starship load could refuel 3 Starships per synod: a single Starship of propellant plant could refuel itself and 5 other Starships over the next ~5 years.

This really surprised me, it's almost exactly the opposite of my preconception and it makes the SpaceX scheme of recovering Starships from Mars seem a lot more efficient. They have the option of quickly scaling up to return all the ships that land, or bringing a lot of stuff like labs, refineries and factories to work towards reducing payload-from-earth requirements while simultaneously building up a propellant plant capable of returning a fraction of the ships.

Best of all, at least my impression is I've done a relatively incompetent job at optimizing for minimal mass, a well-optimized system might require significantly less mass.
