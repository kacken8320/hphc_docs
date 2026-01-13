Structs
=======

.. note::

	This whole thing is a work-in-progress and acts more like notes/brainstorm for myself rather than documentation.

.. code-block:: c

	struct Charm {
		struct Effect[] effect;		/* charm.effect = ritual.effect + emotion.effect;
		int strength;			/* charm.strength = ((medium.strength + ritual.strength) * wizard.complete_power * emotion.modifier); */
	};

		struct Ritual {
			int time;		/* in seconds */
			int execution_quality;	/* 0 - 100 */
			int complexity;		/* 0 - n */
			enum Act act;		/* each enum act has a unique act.modifier (e.g. moving wand has modifier 4, dancing has modifier 40) */
			int strength;		/* time * execution_quality * complexity * act */
		};

		enum Medium {
			NOTHING = 1;
			HAND = 2;
			WAND = 3;
			...
		};

			enum Act {
				CONCENTRATION = 1;
				SAYING_SPELL = 2;
				MOVING_HAND = 3;
				MOVING_WAND = 4;
				...
			};

		struct Effect {
			enum Effect effect;
			int strength;
		};

			/* maybe these should also be structs, e.g. SUMMON_SHIELD should have a location, size, strength, visibility, ... */
			enum Effect {
				MAKE_OBJECT_FLY;
				STUN_RECEIVER;
				SUMMON_SHIELD;
				...
			}

			/* so maybe also like this */
			struct MakeObjectFly {
				int velocity;
				int duration;
				int strength;	// in kg
			};
			struct StunReceiver {
				int duration;
				int direction;
				int strength;	// can it only stun Collin or can it stun Hagrid? Depends on wizard.complete_power
			};
			struct SummonShield {
				(int, int, int) location;
				vector direction;
				int size;
				int strength;
				int visibility;	 // 0 - 255
			};