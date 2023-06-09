##### Crawl Init file ###############################################
# For descriptions of all options, as well as some more in-depth information
# on setting them, consult the file
#    options_guide.txt
# in your /docs directory. If you can't find it, the file is also available
# online at:
# https://github.com/crawl/crawl/blob/master/crawl-ref/docs/options_guide.txt
#
# Crawl uses the first file of the following list as its option file:
#  * init.txt in the -rcdir directory (if specified)
#  * .crawlrc in the -rcdir directory (if specified)
#  * init.txt (in the Crawl directory)
#  * ~/.crawl/init.txt (Unix only)
#  * ~/.crawlrc (Unix only)
#  * ~/init.txt (Unix only)
#  * settings/init.txt (in the Crawl directory)

##### Some basic explanation of option syntax #######################
# Lines beginning with '#' are comments. The basic syntax is:
#
# field = value         or      field.subfield = value
#
# Only one specification is allowed per line.
#
# The terms are typically case-insensitive except in the fairly obvious
# cases (the character's name and specifying files or directories when
# on a system that has case-sensitive filenames).
#
# White space is stripped from the beginning and end of the line, as
# well as immediately before and after the '='. If the option allows
# multiple comma/semicolon-separated terms (such as
# autopickup_exceptions), all whitespace around the separator is also
# trimmed. All other whitespace is left intact.
#
# There are three broad types of Crawl options: true/false values (booleans),
# arbitrary values, and lists of values. The first two types use only the
# simple =, with later options - which includes your options that are different
# from the defaults - overriding earlier ones. List options allow using +=, ^=,
# -=, and = to append, prepend, remove, and reset, respectively. Usually you will
# want to use += to add to a list option. Lastly, there is := which you can use
# to create an alias, like so:
#   ae := autopickup_exceptions
# From there on, 'ae' will be treated as if it you typed autopickup_exceptions,
# so you can save time typing it.
#

##### Other files ###################################################
# You can include other files from your options file using the 'include'
# option. Crawl will treat it as if you copied the whole text of that file
# into your options file in that spot. You can uncomment some of the following
# lines by removing the beginning '#' to include some of the other files in
# this folder.

# Some useful, more advanced options, implemented in LUA.
# include = advanced_optioneering.txt

# Alternative vi bindings for Dvorak users.
# include = dvorak_command_keys.txt

# Alternative vi bindings for Colemak users.
# include = colemak_command_keys.txt

# Alternative vi bindings for Neo users.
# include = neo_command_keys.txt

# Override the vi movement keys with a non-command.
# include = no_vi_command_keys.txt

# Turn the shift-vi keys into safe move, instead of run.
# include = safe_move_shift.txt

##### Ancient versions ##############################################
# If you're used to the interface of ancient versions of Crawl, you may
# get back parts of it by uncommenting the following options:

# include                 = 034_command_keys.txt

# And to revert monster glyph and colouring changes:

# include                 = 052_monster_glyphs.txt
# include                 = 060_monster_glyphs.txt
# include                 = 071_monster_glyphs.txt
# include                 = 080_monster_glyphs.txt
# include                 = 0.9_monster_glyphs.txt
# include                 = 0.12_monster_glyphs.txt
# include                 = 0.13_monster_glyphs.txt
# include                 = 0.14_monster_glyphs.txt

###################
# Quality of life #
###################
explore_auto_rest = true
explore_delay = 10
travel_delay = 10
show_travel_trail = true
show_more = false
default_manual_training = true
autofight_stop = 80
default_manual_training = true

# display low HP warning when [X]% HP or below
hp_warning = 25
##############################


##########################################
# Open skill menu at the start of a game #
##########################################
{

local open_skill_menu = true
function ready()
  if you.turns() == 0 and open_skill_menu then
    open_skill_menu = false
    crawl.sendkeys("m")
    crawl.sendkeys("!")
    crawl.sendkeys("!")
  end
end
}
###############################################


# Set Alias
more := force_more_message
stop := runrest_stop_message

####################
# Dungeon Features #
####################

# Abyssal Rune
more += Found .* abyssal rune of Zot

# Entrances, Exits, and Arrivals
more += Found a frozen archway
more += Found a gateway leading out of the Abyss
more += Found a staircase to the Ecumenical Temple
more += .*resides here

# Portal Timers
more += distant snort
more += interdimensional caravan
more += invites you to visit
more += oppressive heat
more += roar of battle
more += sound of rushing water
more += The drain falls to bits
more += There is an entrance to a bailey on this level
more += tolling of a bell
more += wave of frost
more += You hear the drain falling apart
more += You hear.*crackle.*magical portal
more += You hear.*crackling.*archway
more += You hear.*creaking.*(oriflamme|portcullis)
more += You hear.*hiss.*sand
more += You hear.*rumble.*avalanche
more += You hear.*rusting.*drain
more += You hear.*ticking.*clock
more += You feel a terrible weight on your shoulders

# Traps
more += (blundered into a|invokes the power of) Zot
more += A huge blade swings out and slices into you
stop += An alarm trap emits a blaring wail
stop += found a zot trap
stop += hear a soft click
more += The power of Zot is invoked against you
more += You fall through a shaft
more += You stumble into the trap

# Other
more += Another plant grows acid sacs
more += One of the plants suddenly grows acid sacs
more += The walls and floor vibrate strangely for a moment
more += You are suddenly pulled into a different region
more += You have a vision of.*gates?

###########
# Failure #
###########

more += sense of stasis
more += Something interferes with your magic
more += The spell fizzles
more += The writing blurs in front of your eyes
more += The.*is unaffected
more += This potion can/'t work under stasis
more += You are held in a net
more += You are too injured to fight blindly
more += You can't gag anything down
more += You can't unwield
more += when .*silenced
more += You cannot .* while unable to breathe
more += You cannot .* in your current state
more += You don't have any such object
more += You don't have enough magic
more += You don't.* that spell
more += You fail to use your ability
more += You have no appropriate body parts free
more += no means to grasp
more += You haven't enough magic at the moment
more += You miscast
more += Your amulet of stasis
more += Your attempt to break free
more += Your body armour is too heavy
more += You miscast.*(Blink|Borgnjor|Door|Invisibility)
more += You can't (read|drink|do)
more += There's something in the way
more += There's nothing to (close|open) nearby
more += not good enough to have a special ability
more += You are too berserk
more += That item cannot be evoked
more += You don't have the energy to cast that spell
more += You are unable to access your magic

#############################
# Bad and Unexpected Things #
#############################

#Bad things
more += corrodes your equipment
more += Your corrosive artefact corrodes you
more += are blown away by the wind
more += dispelling energy hits you
more += infuriates you
more += lose consciousness
more += mark forms upon you
more += MASSIVE DAMAGE
more += Ouch! That really hurt!
more += silver sears you
more += Space bends around you
more += Space warps.*around you
more += hits you.*distortion
more += (?!.*(Here|Aim):)^.*wielding.*of distortion
more += surroundings become eerily quiet
more += Terrible wounds (open|spread) all over you
more += The acid corrodes your
more += The air around.*erupts in flames
more += The air twists around and violently strikes you in flight
more += You shudder from the earth-shattering force
more += The arrow of dispersal hits you[^r]
more += The barbed spikes become lodged in your body
more += The barbed spikes dig painfully into your body as you move
more += The blast of calcifying dust hits you[^r]
more += The poison in your body grows stronger
more += The pull of.*song draws you forwards
more += The.*engulfs you in water
more += The.*grabs you[^r]
more += You (are|feel) drained
more += You are (blasted|electrocuted)
more += You are blown backwards
more += You are burned terribly
more += You are encased in ice
more += You are engulfed in calcifying dust
more += You are engulfed in dark miasma
more += You are engulfed in mutagenic fog
more += You are knocked back
more += You are mesmerised
more += You are slowing down
more += You are trampled
more += You convulse
more += You feel a (horrible|terrible) chill
more += You feel haunted
more += You feel less vulnerable to poison
more += You feel your attacks grow feeble
more += You feel your flesh.*rot
more += You feel your power drain away
more += You feel your power leaking away
more += You feel yourself grow more vulnerable to poison
more += You stumble backwards
more += You.*re (confused|more confused|too confused)
more += You.*re (poisoned|more poisoned|lethally poisoned)
more += Your body is wracked with pain
more += Your damage is reflected back at you
more += Your limbs are stiffening
more += Your magical defenses are stripped away
more += Your?.*suddenly stops? moving
more += A sentinel's mark forms upon you
more += Your magical effects are unravelling

# Monsters doing bad things
more += A tree reaches out and hits you!
more += Agitated ravens fly out from beneath the
more += begins to recite a word of recall
more += Being near the torpor snail leaves you feeling lethargic
more += blows on a signal horn
more += cast banishment
more += cast paralyse
more += cast Torment
more += goes berserk
more += The moth of wrath goads something on
more += is duplicated
more += is no longer invulnerable
more += Its appearance distorts for a moment
more += Mara seems to draw the.*out of itself
more += Mara shimmers
more += Miasma billows from the
more += shoots a curare
more += stands defiantly in death's doorway
more += steals.*your
more += swoops through the air toward you
more += The forest starts to sway and rumble
more += The jumping spider pounces on you [^but]
more += The octopode crusher throws you
more += The shadow imp is revulsed by your support of nature
more += The water nymph flows with the water
more += The.*offers itself to Yredelemnul
more += The.*seems to speed up
more += The.*shudders
more += There is a horrible\, sudden wrenching feeling in your soul
more += Vines fly forth from the trees!
more += You are hit by a branch
more += watched by something
more += Your magical defenses are stripped away
more += \'s.*reflects
more += is wielding.*of
more += zaps a wand
more += (He|She|It) is.*carrying a wand of

# Unexpected situations
more += A magical barricade bars your way
#more += Done waiting
more += doors? slams? shut
more += It doesn't seem very happy
more += Mutagenic energies flood into your body
more += Some monsters swap places
more += devoid of blood
more += (The|Your).*falls away!
more += The divine light dispels your darkness!
more += The walls disappear
more += There is a sealed passage
more += You are wearing\:
#more += You can now
more += You cannot afford.*fee
more += You feel (dopey|clumsy|weak)
more += You feel a genetic drift
more += You feel monstrous
more += You feel your rage building
more += You have disarmed
more += You have finished your manual
more += You have reached level
more += You need to eat something NOW
more += You smell decay. (^Yuck!)
more += You stop (a|de)scending the stairs
more += You turn into a fleshy mushroom
more += Your body shudders with the violent release of wild energies
more += Your guardian golem overheats
more += your magic stops regenerating
more += Your scales start
more += your.*devoured
#more += Your?.*can no longer
more += Green shoots are pushing up through the earth
more += Deactivating autopickup
more += Gained mutation
stop += flesh start
stop += Wait a moment

# Things getting better
stop += contamination has completely
more += You can move again
more += You slip out of the net
more += You.*and break free
more += Your fit of retching subsides
more += seems mollified
#more += as sick as possible
more += You now have enough gold to buy
more += skill increases to
more += .*falls from the air

# Ghouls
: if you.race() == "Ghoul" then
    stop += smell.*(rott(ing|en)|decay)
    stop += something tasty in your inventory
: end

##################
# Translocations #
##################

# Teleporting
more += You blink
more += You.*teleport [^f]
more += You feel strangely (unstable|stable)
more += You feel your translocation being delayed
more += Your surroundings flicker
more += Your surroundings seem slightly different
more += Your surroundings suddenly seem different
# -Tele
more += You cannot blink right now
more += You cannot teleport right now
more += You feel.*firmly anchored in space
more += You are no longer firmly anchored in space
# -cTele
more += You feel your control is inadequate

####################
# Expiring Effects #
####################

# God Abilities
# Divine Shield (The Shining One)
more += Your divine shield starts to fade.
more += Your divine shield fades away.
# Jelly Prayer (Jiyva)
more += Your prayer is over.
# Mirror Damage (Yredelemnul)
more += dark mirror aura disappears
# Trog's Hand
more += You feel the effects of Trog's Hand fading
more += You feel less resistant to hostile enchantments
# Heroism
more += You feel like a meek peon again
# Finesse
more += Your hands slow down

# Player Spells
# Aura of Abjuration
stop += Your aura of abjuration expires
# Control Teleport
stop += you feel uncertain
# Death's Door
more += time is quickly running out
more += life is in your own
# Enslavement
more += is no longer charmed
# Flight
more += You are starting to lose your buoyancy
stop += You lose control over your flight
# Haste
more += Your extra speed is starting to run out
more += You feel yourself slow down
# Invisibility
more += You feel more conspicuous
more += You flicker for a moment
more += You flicker back
#stop += You feel more conspicuous
#stop += You flicker for a moment
#stop += You flicker back
# Ozocubu's Armour and Condensation Shield
more += Your icy (shield|armour) evaporates
more += Your.*(shield|armour) melts away
# Phase Shift
more += You feel closer to the material plane
more += You are firmly grounded in the material plane once more
# Repel/Deflect
stop += missiles spell is about to expire
more += You feel less protected from missiles
# Shroud of Golubria
#stop += shroud begins to fray
#stop += shroud unravels
more += Your shroud falls apart
# Silence
more += Your hearing returns
# Swiftness
stop += start to feel a little slower
more += You feel sluggish
# Transmutations
more += Your transformation is almost over
more += Your transformation has ended
more += You have a feeling this form
more += Your skin feels tender
more += You feel yourself come back to life
more += You revert to your normal fleshy form
stop += You revert to your normal fleshy form
# Regeneration
#more += Your skin stops crawling
#more += Your skin is crawling a little less now
# Death channel
more += Your unholy channel is weakening
stop += Your unholy channel is weakening
more += Your unholy channel expires
# Potion of Resistance
more += You start to feel less resistant
more += Your resistance to elements expires
# Naga breath
more += You have got your breath back

############
# Religion #
############

# Gifts or abilities are ready
# Dithmenos
more += You are shrouded in an aura of darkness
more += You now sometimes bleed smoke
more += You.*no longer.*bleed smoke
more += Your shadow no longer tangibly mimics your actions
more += Your shadow now sometimes tangibly mimics your actions
#Fedhas
#more += .*your wandering mushroom
#more += Your wandering mushroom.*
stop += .*your wandering mushroom
stop += Your wandering mushroom.*
# Gozag
more += will now duplicate a non-artefact item
# Jiyva
more += will now unseal the treasures of the Slime Pits
more += Jiyva alters your body
: if not string.find(you.god(), "Jiyva") then
  more += splits in two
:end
# Kikubaaqudgha
more += Kikubaaqudgha will now enhance your necromancy
# Lugonu
more += Lugonu will now corrupt your weapon
# Qazlal
more += resistances upon receiving elemental damage
more += You are surrounded by a storm which can block enemy attacks
# Ru
more += you are ready to make a new sacrifice
# Sif Muna
more += Sif Muna is protecting you from the effects of miscast magic
# The Shining One
more += The Shining One will now bless
# Zin
more += will now cure all your mutations
# You Screwed Up
more += is no longer ready
#Yred
more += soul is now ripe for the taking
more += soul is no longer ripe for the taking
# Vehumet spell gift
more += Vehumet offers you knowledge
# Xom
more += staircase.*moves
more += is too large for the net to hold
: if you.god() == "Xom" then
    more += god:
: end
: if you.god() == "Xom" then
    stop += god:
: end

# Poor Decisions
more += You really shouldn't be using

# Wrath
more += Nemelex gives you another card to finish dealing
more += Fedhas invokes the elements against you
more += Lugonu sends minions to punish you
more += Okawaru sends forces against you
more += wrath finds you
stop += wrath finds you


################
# Hell Effects #
################

more += hell effect:
more += A gut-wrenching scream fills the air
more += Brimstone rains from above
more += Die\, mortal
more += Leave now\, before it is too late
more += Something frightening happens
more += Trespassers are not welcome here
more += We do not forgive those who trespass against us
more += We have you now
more += You do not belong in this place
more += You feel a terrible foreboding
more += You feel lost and a long\, long way from home
more += You hear diabolical laughter
more += You hear words spoken in a strange and terrible language
more += You sense a hostile presence
more += You sense an ancient evil watching you
more += You shiver with fear
more += You smell brimstone
more += You suddenly feel all small and vulnerable
more += You will not leave this place

############
# Monsters #
############

# Arriving Unexpectedly
more += appears in a shower of sparks
more += appears out of thin air
more += comes (up|down) the stairs
more += Something appears in a flash of light
more += The.*is a mimic
more += You sense the presence of something unfriendly
more += The.*answers the.*call
more += Wisps of shadow swirl around
more += Shadows whirl around

# Item Use
more += drinks a potion
more += evokes.*(amulet|ring)
more += reads a scroll
more += zaps a (wand|rod)

# Terrible Monsters
more += 's ghost.*(comes? into view|opens the)
more += A player ghost.*(comes? into view|opens the)
more += boggarts?.*(comes? into view|opens the)
more += curse skull.*comes? into view
more += .*fiend.*(comes? into view|opens the)
more += flayed ghost.*(comes? into view|opens the)
more += giant eyeball.*comes? into view
more += giant orange brains?.*(comes? into view|opens the)
more += giant spore.*comes? into view
more += hellion.*(comes? into view|opens the)
more += tzitzimitl.*(comes? into view|opens the)
more += Lich.*(comes? into view|opens the)
more += Ancient Lich.*(comes? into view|opens the)
more += orange crystal statue.*comes? into view
more += shadow demons?.*(comes? into view|opens the)
more += silver statue.*comes? into view
more += tormentor.*(comes? into view|opens the)
more += .*shrike.* comes? into view
more += curse toe.*comes? into view
more += entropy weaver.*(comes? into view|opens the)
more += goliath frog.*comes? into view
more += bloated husk.*comes? into view
more += fenstrider witch.*(comes? into view|opens the)
more += moth of wrath.*comes? into view
more += .*orbs? of fire.*comes? into view
more += .*hell sentinel.*(comes? into view|opens the)
more += .*neqoxec.*(comes? into view|opens the)
more += .*cacodemon.*(comes? into view|opens the)
more += .*greater mummy.*(comes? into view|opens the)
more += .*mummy priest.*(comes? into view|opens the)
more += .*lurking horror.*(comes? into view|opens the)
more += .*ogre mage.*(comes? into view|opens the)
more += .*a wizard.*(comes? into view|opens the)
more += .*orc sorcerer.*(comes? into view|opens the)
more += .*sphinx.*(comes? into view|opens the)
more += .*great orb of eyes.*comes? into view
more += ((floating|shining) eye|dream sheep|death drake).*into view
more += (wretched star|apocalypse crab).*into view
more += torpor snail.*comes? into view
more += spriggan druid.*(comes? into view|opens the)
more += (vault (warden|sentinel)|merfolk (avatar|siren)).*(comes? into view|opens the)
more += (guardian serpent|draconian (shifter|scorcher|annihilator)|convoker|death cob).*(comes? into view|opens the)
more += (phantasmal warrior|air elemental).*(comes? into view|opens the)
more += (vampire knight|basilisk|deep elf (sorcerer|demonologist|high priest|annihilator)).*(comes? into view|opens the)
more += tengu reaver.*(comes? into view|opens the)
more += juggernaut.*(comes? into view|opens the)

# Uniques
# This line is supposed to do them all (including pan lords)
more += (?-i:[A-Z]).* comes? into view

# more += 27-headed.*(comes? into view|opens the)
# more += Agnes.*(comes? into view|opens the)
# more += Aizul.*(comes? into view|opens the)
# more += Antaeus.*(comes? into view|opens the)
# more += Arachne.*(comes? into view|opens the)
# more += Asmodeus.*(comes? into view|opens the)
# more += Asterion.*(comes? into view|opens the)
# more += Azrael.*(comes? into view|opens the)
# more += Blork the orc.*(comes? into view|opens the)
# more += Boris.*(comes? into view|opens the)
# more += Cerebov.*(comes? into view|opens the)
# more += Crazy Yiuf.*(comes? into view|opens the)
# more += Dispater.*(comes? into view|opens the)
# more += Dissolution.*(comes? into view|opens the)
# more += Donald.*(comes? into view|opens the)
# more += Dowan.*(comes? into view|opens the)
# more += Duvessa.*(comes? into view|opens the)
# more += Edmund.*(comes? into view|opens the)
# more += Ereshkigal.*(comes? into view|opens the)
# more += Erica.*(comes? into view|opens the)
# more += Erolcha.*(comes? into view|opens the)
# more += Eustachio.*(comes? into view|opens the)
# more += Fannar.*(comes? into view|opens the)
# more += Frances.*(comes? into view|opens the)
# more += Frederick.*(comes? into view|opens the)
# more += Gastronok.*(comes? into view|opens the)
# more += Geryon.*(comes? into view|opens the)
# more += Gloorx Vloq.*(comes? into view|opens the)
# more += Grinder.*(comes? into view|opens the)
# more += Grum.*(comes? into view|opens the)
# more += Harold.*(comes? into view|opens the)
# more += Ignacio.*(comes? into view|opens the)
# more += Ijyb.*(comes? into view|opens the)
# more += Ilsuiw.*(comes? into view|opens the)
# more += Jessica.*(comes? into view|opens the)
# more += Jorgrun.*(comes? into view|opens the)
# more += Jory.*(comes? into view|opens the)
# more += Joseph.*(comes? into view|opens the)
# more += Josephine.*(comes? into view|opens the)
# more += Khufu.*(comes? into view|opens the)
# more += Kirke.*(comes? into view|opens the)
# more += Lom Lobon.*(comes? into view|opens the)
# more += Louise.*(comes? into view|opens the)
# more += Maggie.*(comes? into view|opens the)
# more += Mara.*(comes? into view|opens the)
# more += Margery.*(comes? into view|opens the)
# more += Maurice.*(comes? into view|opens the)
# more += Menkaure.*(comes? into view|opens the)
# more += Mennas.*(comes? into view|opens the)
# more += Mnoleg.*(comes? into view|opens the)
# more += Murray.*(comes? into view|opens the)
# more += Natasha.*(comes? into view|opens the)
# more += Nergalle.*(comes? into view|opens the)
# more += Nessos.*(comes? into view|opens the)
# more += Nikola.*(comes? into view|opens the)
# more += Pikel.*(comes? into view|opens the)
# more += Polyphemus.*(comes? into view|opens the)
# more += Prince Ribbit.*(comes? into view|opens the)
# more += Psyche.*(comes? into view|opens the)
# more += Purgy.*(comes? into view|opens the)
# more += Robin.*(comes? into view|opens the)
# more += Roxanne.*(comes? into view|opens the)
# more += Rupert.*(comes? into view|opens the)
# more += Saint Roka.*(comes? into view|opens the)
# more += Sigmund.*(comes? into view|opens the)
# more += Snorg.*(comes? into view|opens the)
# more += Sojobo.*(comes? into view|opens the)
# more += Sonja.*(comes? into view|opens the)
# more += Terence.*(comes? into view|opens the)
# more += The Lernaean hydra.*(comes? into view|opens the)
# more += The royal jelly.*(comes? into view|opens the)
# more += The Serpent of Hell.*(comes? into view|opens the)
# more += Tiamat.*(comes? into view|opens the)
# more += Urug.*(comes? into view|opens the)
# more += Vashnia.*(comes? into view|opens the)
# more += Xtahua.*(comes? into view|opens the)
###############################################


########################
# Minimap color scheme #
########################
tile_upstairs_col = #99ff33
tile_downstairs_col = #ff1a1a
tile_branchstairs_col = #ff1a1a
tile_portal_col = #ff1a1a
tile_door_col = #cb6d4d
tile_wall_col = #595959
tile_explore_horizon_col = #bfbfbf
tile_floor_col = #262626
tile_item_col = #262626
tile_feature_col = #d4be21
tile_plant_col = #5c8745
tile_water_col = #0086b3
tile_deep_water_col = #1f1fed
tile_trap_col = #d24dff
tile_transporter_col = #ff80bf
tile_transporter_landing_col = #59ff89
tile_lava_col = #6f0b00
###############################################

