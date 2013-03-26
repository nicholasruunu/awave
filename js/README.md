# js/jQuery

## Standard template

```js
	"use strict";
	// En själv-exekverande function (closure) används för att
	// försäkra sig om att ingen ändrat på de viktigaste variablerna
	(function ($, Drupal, window, document, undefined) {

		// jQuery ready (Sidan har laddats)
		$(function() {

			// En javascript modul på sidan
			// Varje javascript del ska vara enkapsulerad med själv-
			// exekverande closure samt vara kommenterad
			(function() {
				// jQuery objekt prefixas med $
				// Containern ska helst ha ett id
				var $container = $('#slider-container');
				var $images = $container.find('.slider-images');
				var $display = $container.find('.slider-display');
				var $next_button = $container.find('.slider-next');
				// Vid vanliga värden så utesluts $
				var container_height = $container.outerHeight();

				$images.each(function() {
					// Om $(this) anropas flera gånger, cacha i variabel
					var $this = $(this);
					// Bygg upp vad som behövs
					$this.css({ color: 'black', background: 'white' });

					// Använd aldrig px, jQuery förstår heltal
					$this.height(container_height);
				});

				$display.bind({
					show: function() {
						// Visa bilden
						...
					},

					next: function() {
						// Nästa bild
						...
					}
				});

				// Registrera events
				$next_button.click(function() {
					$display.trigger('next');
				});

				$display.trigger('show');
			})();
		});

	}(jQuery, Drupal, this, this.document));

``
