<script>
	import { spring } from 'svelte/motion';

	let count = 0;

	const displayed_count = spring();
	$: displayed_count.set(count);
	$: offset = modulo($displayed_count, 1);

	/**
	 * @param {number} n
	 * @param {number} m
	 */
	function modulo(n, m) {
		// handle negative numbers
		return ((n % m) + m) % m;
	};

	var imageUrls = [
        "src\routes\img.jpg",
        "src\routes\shahd-1.gif",
        "src\routes\image.jpg",
        "src\routes\21st-birthday-9.gif"
    ];

    // Get the button and image elements
    var counterButton = document.getElementById('counter button');
    var imageElement = document.getElementById('image');

    // Counter to keep track of the current image index
    var counter = 0;

    // Function to update the image source
    function updateImage() {
        imageElement.src = imageUrls[counter];
    }

    // Initial image update
    updateImage();

    // Event listener for the counter button
    counterButton.addEventListener('click', function () {
        // Increment the counter and wrap around if it exceeds the array length
        counter = (counter + 1) % imageUrls.length;
        // Update the image
        updateImage();
    });
</script>

<div class="counter">
	<button id="counter button" on:click={() => (count -= 1)} aria-label="Decrease the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5" />
		</svg>
	</button>

	<div class="counter-viewport">
		<div class="counter-digits" style="transform: translate(0, {100 * offset}%)">
			<!-- <strong class="hidden" aria-hidden="true">{Math.floor($displayed_count + 1)}</strong> -->
			<strong>
				<img id="image" src="" alt="Image">
			</strong>
		</div>
	</div>

	<button id="counter button" on:click={() => (count += 1)} aria-label="Increase the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
		</svg>
	</button>
</div>

<style>
	.counter {
		display: flex;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	}
	.counter button {
		width: 2em;
		padding: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 0;
		background-color: transparent;
		touch-action: manipulation;
		font-size: 2rem;
	}

	.counter button:hover {
		background-color: var(--color-bg-1);
	}

	svg {
		width: 25%;
		height: 25%;
	}

	path {
		vector-effect: non-scaling-stroke;
		stroke-width: 2px;
		stroke: #444;
	}

	.counter-viewport {
		width: 8em;
		height: 4em;
		overflow: hidden;
		text-align: center;
		position: relative;
	}

	.counter-viewport strong {
		position: absolute;
		display: flex;
		width: 100%;
		height: 100%;
		font-weight: 400;
		color: var(--color-theme-1);
		font-size: 4rem;
		align-items: center;
		justify-content: center;
	}

	.counter-viewport strong img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
	}

	.counter-digits {
		position: absolute;
		width: 100%;
		height: 100%;
	}

	.hidden {
		top: -100%;
		user-select: none;
	}
</style>
