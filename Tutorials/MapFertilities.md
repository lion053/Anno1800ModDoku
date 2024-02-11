Got permission to copy this via discord.

[15:53]Hier0nimus: @Artwork 
Fertilities are defined for every island and depend on the type of island (Starter, normal(large?), medium, small). A starter island for example always has potatoes and oil.
When a region is entered (Start of the game > Old World, New World at Artisans, ect) A list of islands is choosen by the game. With the choice of those islands the game also defines the fertilities. Those can not be changed after this point unless you start a new game. 
[15:55]Hier0nimus: Which islands the game chooses depends on the settings you choose at the setup of the game. If you choose a harder setting, the game will take other types of islands. Again, once you choose that setting at that point, no way to change it after that point unless you start a new game.
[15:58]Hier0nimus: Every setting has different combinations of islands AND fertilities.Those combinations are combines in POOLS and those islands in those pools use FERTILITYSETS.
[15:58]Hier0nimus: On https://www.a1800.net/ you can search for example for GUID "141508". This is from the template "FertilitySet" with the name "Set 1".
[15:59]Hier0nimus: If you look at the XML view and try to understand the code you can find a lot of information there and it tells you exactly what it does.
[15:59]Hier0nimus: <Asset>
    <Template>FertilitySet</Template>
    <Values>
        <Standard>
            <GUID>141508</GUID>
            <Name>Set 1</Name>
        </Standard>
        <ResourceSetCondition>
            <AllowedRegion>Moderate</AllowedRegion>
            <AllowedIslandType>Normal;Starter</AllowedIslandType>
            <AllowedIslandDifficulty>Normal;Hard</AllowedIslandDifficulty>
            <AllowedResourceAmounts>Low</AllowedResourceAmounts>
        </ResourceSetCondition>
        <FertilitySet>
            <Fertilities>
                <Item>
                    <Fertility>1010569</Fertility>
                    <!--Potato Fertility-->
                </Item>
                <Item>
                    <Fertility>1010571</Fertility>
                    <!--Grain Fertility-->
                </Item>
            </Fertilities>
        </FertilitySet>
    </Values>
</Asset>
[16:00]Hier0nimus: Like I said:
<Template>FertilitySet</Template>
[16:01]Hier0nimus: If you would look inside the assets.xml or on a1800.net you will find 121 different fertility sets
[16:01]Hier0nimus:
Image
[16:02]Hier0nimus: If we go back to the set I posted above, and we go a bit down, we can see <ResourceSetCondition>
[16:03]Hier0nimus: This defines the conditions for this set. 
<AllowedRegion>Moderate</AllowedRegion>  > The region this set is used is in the moderate region, which is Old World and Cape. If we would add the New World and/or Arctic, New World and Enbesa here, this would make those fertilities also there avaialble. 
[16:05]Hier0nimus: <AllowedIslandType>Normal;Starter</AllowedIslandType> > This tells us on which island types this set is used. Normal or Starter. The starter island is the one you will get a harbor when you choose as starting conditions "Harbour". Normal are the island which have the same size as the started island but have some things less because started islands are given some fixed things like oil.
[16:06]Hier0nimus: <AllowedIslandDifficulty>Normal;Hard</AllowedIslandDifficulty> This tells us on which Diffifulty setting this fertilityset is used. Only when you choose Normal or Hard, this set will be added to a Normal or Started island. If you choose "Easy" settings, this fertilityset will not be used.
[16:07]Hier0nimus: <AllowedResourceAmounts>Low</AllowedResourceAmounts> Here we see another setting that is defined when you setup the game, the Allowed resources. When this setting is set to LOW, this fertilityset will be used. Otherwise if you would habe choosen PLENTY and the other I can not remember at the moment. This set will not be given to an island.
[16:11]Hier0nimus: We have taken a look at the <ResourceSetCondition>, now let's go a bit down and take a look at <FertilitySet>
[16:11]Hier0nimus: We see there 2 fertilities, Potato and Grain.
[16:12]Hier0nimus: So, if this fertilityset is given to an island, that island will have potatoes and Grain as fertilities.
[16:13]Hier0nimus: We now have analysed 1 of the 121 fertilitysets. Ever set has their own settings based on all the mentioned above proporties.
[16:13]Hier0nimus: ------------------
[16:15]Hier0nimus: In your case there are I think a couple possibilities:
[16:15]Hier0nimus: 1: You overwrite every 121 fertilitysets removing the ones you do not want with a ModOp Type="remove". Leaving only 1  fertility in every set.
[16:16]Hier0nimus:
If you want to give yourself a bit less work, you could define which difficultysetting you will play and only adapt the ones that your difficultysetting would use. For example, only adapt the ones from the "Low" AllowedResourceAmounts. Do know that this Low Resource amount also affects Mines! And mines is a completly other path ... 😄
[16:18]Hier0nimus: 3: (Maybe the easiest) Remove ALL fertilitysets with a ModOp Type="remove" and then add 1 fertilityset for every type of fertility. Then you build them all up in combination with the right conditions. 
[16:18]Hier0nimus: Well...
[16:18]Hier0nimus: Now that I think about it...
[16:19]Hier0nimus: In theory your idea sounds ok, but to be honest... after writing all that info. I do not think that would be fun to play with 
[16:20]Hier0nimus: The reason is that there are a lot of fertilities. Only providing 1 fertility / island is really restrictive. If you would throw AI in the mix, that is just not going to work.
[16:20]Hier0nimus: You could say that you have to conquer an island to get the fertility, but the limitation will be the randomly choosen fertilities by the game.
[16:21]Hier0nimus: The reason there are at least 2 fertilities / island is because if you only have 1 fertility there is a big change that the game does not roll certain fertilities on ANY island.
[16:21]Hier0nimus: And then... well... then you are in trouble. AI will also not advance because they do not have certain fertilities. 
[16:21]Hier0nimus: Unless you are ok with it that you need to use the fertility items to get a fertility. But AI do not use those. 
[16:22]Hier0nimus: You could say, "I'll just rerstart the game if I do not have a fertiliy on an island"
[16:23]Hier0nimus: But... that would only work if you would already know what you will get in the Arctic, New World and Enbesa. The Old World you can see, but the other regions you only know later when you have already invested a lot of time into that game. You could use the "testmod" where you can enter every region from the start to see if all the islands provide the right fertilities. But that would be a lot of work if you need to restart over and over again untill you find the seed that gives you at least 1 fertility on every island in every region. If you do that, make sure to write down your seed every time and if you found the correct seed, RESTART the game WITHOUT the testmod. That mod breaks things in the game if you use it to actually play. 
[16:23]Hier0nimus: Well. I think I can conclude that this is enough wall of text xD