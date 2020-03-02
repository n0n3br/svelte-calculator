<main>
	<div class='container vh-100'>
		<div class='row h-100'>
			<div class='col-md-4 offset-md-4 col-8 offset-2 bg-light body my-auto border border-dark rounded'>
				<div class='row mt-3 ml-2 mr-2'>
					<div class='col'>
						<Logo />
						<Display current={current} />
						<Keyboard keys={keys} />
					</div>
				</div>
			</div>
		</div>
	</div>
</main>



<script>
  import Display from "./Display.svelte";
  import Keyboard from "./Keyboard.svelte";
  import Logo from "./Logo.svelte";
  import uid from "./utils/uid";
  let acumulator = 0;
  let operation = null;
  let display = "0";

  $: current = parseFloat(display);

  const clear = () => {
    display = String(operation ? acumulator : 0);
    operation = null;
  };

  const clearAll = () => {
    display = "0";
    operation = null;
    acumulator = 0;
  };
  const addDecimal = () => (display += display.includes(".") ? "" : ".");

  const applyOperation = operation => {
    // switch (operation) {
    //   case "+":
    //     current += acumulator;
    //     break;
    //   case "-":
    //     current -= acumulator;
    //     break;
    //   case "/":
    //     current = acumulator / current;
    //     break;
    //   case "*":
    //     current = acumulator * current;
    //     break;
    // }
    // acumulator = current;
  };
  const addDigit = digit => (display += digit);

  const keys = [
    { label: "", id: uid() },
    { label: "", id: uid() },
    { label: "AC", id: uid(), color: "warning", click: clearAll },
    { label: "C", id: uid(), color: "warning", click: clear },
    { label: "7", id: uid(), click: addDigit },
    { label: "8", id: uid(), click: addDigit },
    { label: "9", id: uid(), click: addDigit },
    { label: "+", id: uid(), color: "primary", click: applyOperation },
    { label: "4", id: uid(), click: addDigit },
    { label: "5", id: uid(), click: addDigit },
    { label: "6", id: uid(), click: addDigit },
    { label: "-", id: uid(), color: "primary", click: applyOperation },
    { label: "3", id: uid(), click: addDigit },
    { label: "2", id: uid(), click: addDigit },
    { label: "1", id: uid(), click: addDigit },
    { label: "x", id: uid(), color: "primary", click: applyOperation },
    { label: "0", id: uid(), click: addDigit },
    { label: ".", id: uid(), color: "primary", click: addDecimal },
    { label: "=", id: uid(), color: "primary", click: applyOperation },
    { label: "/", id: uid(), color: "primary", click: applyOperation }
  ];
</script>