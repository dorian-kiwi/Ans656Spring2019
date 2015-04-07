
Basic Concepts
==============

Crossingover and Recombination
------------------------------

An odd number of crossovers between two loci results in a recombination
between them. Because crossing over takes place at random, the
probability of recombination is higher for loci that are farther apart
than for loci that are closer to each other. This provides the basis for
genetic linkage analysis, where recombination rates between loci are
used to order genes on chromosomes. For example, if the recombination
rate between locus $A$ and $B$ is $r_{AB}=0.1$, between $B$ and $C$ is
$r_{BC}=0.1$, and between $A$ and $C$ is $r_{AC}=0.19$, we can arrange
the loci in the order $ABC$. Note that $r_{AC}<r_{AB}+r_{BC}$. This is
because recombinations between $A$ and $B$ and between $B$ and $C$
result in an even number of crossovers between $A$ and $C$ with no
recombination between $A$ and $C$.

Interference
------------

Interference is the lack of independence in recombinations at different
intervals on a chromosome. Consider three loci ordered as $ABC$. If
recombination in the $A$-$B$ interval is independent from recombination
in the $B$-$C$ interval, the probability of a double recombinant,
denoted by $g_{11}$, is $$g_{11}=r_{AB}r_{BC}$$ where $r_{ij}$ is the
probability of a recombination between loci $i$ and $j$. If
recombinations in the two intervals are not independent, the above
probability is give by

$$g_{11}=cr_{AB}r_{BC}$$

where $c$ is called the coefficient of coincidence. Interference is
quantified as $I=1-c$. Thus, under independence, $c=1$ and $I=0$.

Map Distance
------------

The map distance $x$ between two loci, in Morgan units, is defined as
the expected number of crossovers between them. *Unlike recombination
rates, map distances are additive.*

Map distances between loci provide a convenient set of parameters for
models used in linkage analysis. Consider the gametes produced by a
parent heterozygous at each of $k$ loci. Each such gamete corresponds to
a recombination event that can be indexed by a $(k-1)\times1$ vector
 where element $j$ of  is $1$ if there was a recombination between locus
$j$ and $j+1$ or is $0$ otherwise. Thus, in linkage analysis with $k$
loci, there are $2^{k-1}$ recombination events that need to be modeled.
The probability of each of these recombination events can be treated as
a parameter. Taking into consideration that these probabilities sum to
one, this approach would give rise to $2^{k-1}-1$ parameters that need
to be estimated. However, using the relationship between map distance
and recombination rate, probabilities of the $2^{k-1}$ recombination
events can be computed from the $k-1$ map distances between adjacent
loci. Then, these $k-1$ map distances become the parameters for linkage
analysis. The relationship between map distance and recombination rate
is discussed next.

Map Functions
-------------

Map functions provide a transformation from map distance to
recombination rate. Two approaches have been used to derive map
functions. In the first, a probability model is assumed for the number
of crossovers in an interval of length $x$. Then, recombination rate is
calculated as the probability of an odd number of crossovers in the
interval. In the second approach, recombination events in two adjacent
intervals are modeled, allowing for interference. This model is then
used to develop a differential equation, the solution for which yields
the map function. Both of these approaches are described in detail
below.

Suppose that $P_{t}$ is the probability of $t$ crossovers in a
chromosomal interval of length $x$ Morgans. Recall that a recombination
is observed when an odd number of crossovers occurs in this interval.
Thus, probability $r_{x}$ of a recombination in an interval of length
$x$ is

$$
\begin{align}
r_{x}
& =& P_{1}+P_{3}+P_{5}+\cdots\\
& =& {\frac{1}{2}}(1-\sum_{t}P_{t}(-1)^{t})\\
& =& {\frac{1}{2}}(1-P(-1))
\end{align}
$$

where $P(S)=\sum_{t}P_{t}S^{t}$ is the *probability generating function* of the
distribution of crossovers.

Haldane(Haldane.JBS:1919) used the Poisson distribution for $P_{t}$.
This implies that crossovers in one interval are independent of those in
another and that the probability of crossovers in a very short interval
is proportional to the length of the interval. According to the Poisson
distribution, the probability of $t$ crossovers in an interval of length
of $x$ (in Morgan units) is

$$P_{t}=\frac{(\lambda x)^{t}e^{-\lambda x}}{t!}$$

The parameter $\lambda$ in the Poisson distribution is the expected
number of outcomes in a unit interval. Because map distance between two
loci is defined as the expected number of crossovers between them,
$\lambda=1$, and

$$
P_{t}=\frac{x^{t}e^{-x}}{t!}\tag{4}
$$

The probability generating function for (4) is


$$\begin{split}
P(S)
& =\sum_{t}\frac{x^{t}e^{-x}S^{t}}{t!}\\
& =\sum_{t}\frac{(xS)^{t}e^{-xS}}{t!}\frac{e^{-x}}{e^{-xS}}\\
& =e^{x(S-1)}
\end{split}
\tag{5}
$$

Using (5) in (2) gives **Haldane’s map function**:


>$$
r_{x}={\frac{1}{2}}(1-e^{-2x})
\tag{6}
$$

The inverse of (6) is

$$x=\begin{cases}
-{\frac{1}{2}}\ln(1-2r_{x}) & {if  {0\leq r_{x}<{{\frac{1}{2}}}}}\\
\infty & if  {r_{x}={{\frac{1}{2}}}}
\end{cases}$$

Karlin (@Karlin.S:1984) used the binomial distribution with
parameters $N$ and $p$ for $P_{t}$. Thus, $t$ is the number of successes
in $N$ Bernoulli trials each having probability $p$ of success. From the
definition of map distance, it follows that the map distance
$x={\mbox{E}}(t)=Np$, and $p=x/N$. Now, the probability of $t$
crossovers in an interval of length of $x$ is

$$
P_{t}=\binom{N}{t}(x/N)^{t}(1-x/N)^{N-t}
\tag{7}
$$

The probability generating function for (7) is

$$\begin{split}
P(S)
& =\sum_{t}\binom{N}{t}(x/N)^{t}(1-x/N)^{N-t}S^{t}\\
& =\sum_{t}\binom{N}{t}(xS/N)^{t}(1-x/N)^{N-t}\\
& =[xS/N+(1-x/N)]^{N}
\end{split}
\tag{8}
$$

because $\sum_{t}\binom{N}{t}a^{t}b^{N-t}=(a+b)^{N}$. Using
(8) in (2) gives the **binomial map function (Karlin's map function)**:

>$$r_{x}=
\begin{cases}
{{\frac{1}{2}}}[1-(1-2x/N)^{N}]
& {if x<N/2}\\
{{\frac{1}{2}}}
& {if x \geq N/2}
\end{cases}
\tag{9}
$$


    using Gadfly, Reactive, Interact


<script charset="utf-8">(function ($, undefined) {

    function createElem(tag, attr, content) {
	// TODO: remove jQuery dependency
	var el = $("<" + tag + "/>").attr(attr);
	if (content) {
	    el.append(content);
	}
	return el[0];
    }

    // A widget must expose an id field which identifies it to the backend,
    // an elem attribute which is will be added to the DOM, and
    // a getState() method which returns the value to be sent to the backend
    // a sendUpdate() method which sends its current value to the backend
    var Widget = {
	id: undefined,
	elem: undefined,
	label: undefined,
	getState: function () {
	    return this.elem.value;
	},
	sendUpdate: undefined
    };

    var Slider = function (typ, id, init) {
	var attr = { type:  "range",
		     value: init.value,
		     min:   init.min,
		     max:   init.max,
		     step:  init.step },
	    elem = createElem("input", attr),
	    self = this;

	elem.onchange = function () {
	    self.sendUpdate();
	}

	this.id = id;
	this.elem = elem;
	this.label = init.label;

	InputWidgets.commInitializer(this); // Initialize communication
    }
    Slider.prototype = Widget;

    var Checkbox = function (typ, id, init) {
	var attr = { type: "checkbox",
		     checked: init.value },
	    elem = createElem("input", attr),
	    self = this;

	this.getState = function () {
	    return elem.checked;
	}
	elem.onchange = function () {
	    self.sendUpdate();
	}

	this.id = id;
	this.elem = elem;
	this.label = init.label;

	InputWidgets.commInitializer(this);
    }
    Checkbox.prototype = Widget;

    var Button = function (typ, id, init) {
	var attr = { type:    "button",
		     value:   init.label },
	    elem = createElem("input", attr),
	    self = this;
	this.getState = function () {
	    return null;
	}
	elem.onclick = function () {
	    self.sendUpdate();
	}

	this.id = id;
	this.elem = elem;
	this.label = init.label;

	InputWidgets.commInitializer(this);
    }
    Button.prototype = Widget;

    var Text = function (typ, id, init) {
	var attr = { type:  "text",
		     placeholder: init.label,
		     value: init.value },
	    elem = createElem("input", attr),
	    self = this;
	this.getState = function () {
	    return elem.value;
	}
	elem.onkeyup = function () {
	    self.sendUpdate();
	}

	this.id = id;
	this.elem = elem;
	this.label = init.label;

	InputWidgets.commInitializer(this);
    }
    Text.prototype = Widget;

    var Textarea = function (typ, id, init) {
	var attr = { placeholder: init.label },
	    elem = createElem("textarea", attr, init.value),
	    self = this;
	this.getState = function () {
	    return elem.value;
	}
	elem.onchange = function () {
	    self.sendUpdate();
	}

	this.id = id;
	this.elem = elem;
	this.label = init.label;

	InputWidgets.commInitializer(this);
    }
    Textarea.prototype = Widget;

    // RadioButtons
    // Dropdown
    // HTML
    // Latex

    var InputWidgets = {
	Slider: Slider,
	Checkbox: Checkbox,
	Button: Button,
	Text: Text,
	Textarea: Textarea,
	debug: false,
	log: function () {
	    if (InputWidgets.debug) {
		console.log.apply(console, arguments);
	    }
	},
	// a central way to initalize communication
	// for widgets.
	commInitializer: function (widget) {
	    widget.sendUpdate = function () {};
	}
    };

    window.InputWidgets = InputWidgets;

})(jQuery, undefined);
</script>



<script charset="utf-8">(function (IPython, $, _, MathJax, Widgets) {
    $.event.special.destroyed = {
	remove: function(o) {
	    if (o.handler) {
		o.handler.apply(this, arguments)
	    }
	}
    }

    var redrawValue = function (container, type, val) {
	var selector = $("<div/>");
	var oa = new IPython.OutputArea(_.extend(selector, {
	    selector: selector,
	    prompt_area: true,
	    events: IPython.events,
	    keyboard_manager: IPython.keyboard_manager
	})); // Hack to work with IPython 2.1.0

	switch (type) {
	case "image/png":
            var _src = 'data:' + type + ';base64,' + val;
	    $(container).find("img").attr('src', _src);
	    break;
	default:
	    var toinsert = IPython.OutputArea.append_map[type].apply(
		oa, [val, {}, selector]
	    );
	    $(container).empty().append(toinsert.contents());
	    selector.remove();
	}
	if (type === "text/latex" && MathJax) {
	    MathJax.Hub.Queue(["Typeset", MathJax.Hub, toinsert.get(0)]);
	}
    }


    $(document).ready(function() {
	Widgets.debug = false; // log messages etc in console.
	function initComm(evt, data) {
	    var comm_manager = data.kernel.comm_manager;
	    comm_manager.register_target("Signal", function (comm) {
		comm.on_msg(function (msg) {
		    //Widgets.log("message received", msg);
		    var val = msg.content.data.value;
		    $(".signal-" + comm.comm_id).each(function() {
			var type = $(this).data("type");
			if (val[type]) {
			    redrawValue(this, type, val[type], type);
			}
		    });
		    delete val;
		    delete msg.content.data.value;
		});
	    });

	    // coordingate with Comm and redraw Signals
	    // XXX: Test using Reactive here to improve performance
	    $([IPython.events]).on(
		'output_appended.OutputArea', function (event, type, value, md, toinsert) {
		    if (md && md.reactive) {
			// console.log(md.comm_id);
			toinsert.addClass("signal-" + md.comm_id);
			toinsert.data("type", type);
			// Signal back indicating the mimetype required
			var comm_manager = IPython.notebook.kernel.comm_manager;
			var comm = comm_manager.comms[md.comm_id];
			comm.send({action: "subscribe_mime",
				   mime: type});
			toinsert.bind("destroyed", function() {
			    comm.send({action: "unsubscribe_mime",
				       mime: type});
			});
		    }
	    });

	    // Set up communication for Widgets
	    Widgets.commInitializer = function (widget) {
		var comm = comm_manager.new_comm(
		    "InputWidget", {widget_id: widget.id}
		);
		widget.sendUpdate = function () {
		    // `this` is a widget here.
		    // TODO: I have a feeling there's some
		    //       IPython bookkeeping to be done here.
		    // Widgets.log("State changed", this, this.getState());
		    comm.send({value: this.getState()});
		}
	    };
	}

	try {
	    // try to initialize right away. otherwise, wait on the status_started event.
	    initComm(undefined, IPython.notebook);
	} catch (e) {
	    $([IPython.events]).on('status_started.Kernel', initComm);
	}
    });
})(IPython, jQuery, _, MathJax, InputWidgets);
</script>



    @manipulate for N=2:10
        plot([x -> x<N/2 ? 0.5(1 - (1 - 2x/N)^N):0.5, x -> 0.5(1 - exp(-2x))] , 0,2.0, 
        Guide.title("Karlin's (f<sub>1</sub>) and Haldane's (f<sub>2</sub>) Map Functions"),
            Guide.ylabel("Recombination Rate"), Guide.xlabel("Map Distance"),
            Guide.colorkey("Map Function")
        )
    end








<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg"
     xmlns:xlink="http://www.w3.org/1999/xlink"
     xmlns:gadfly="http://www.gadflyjl.org/ns"
     version="1.2"
     width="141.42mm" height="100mm" viewBox="0 0 141.42 100"
     stroke="none"
     fill="#000000"
     stroke-width="0.3"
     font-size="3.88"

     id="fig-371e21ceeb8a4893938846e9321c8d7c">
<g class="plotroot xscalable yscalable" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-1">
  <g font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" fill="#564A55" stroke="none" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-2">
    <text x="66.2" y="92" text-anchor="middle">Map Distance</text>
  </g>
  <g class="guide xlabels" font-size="2.82" font-family="'PT Sans Caption','Helvetica Neue','Helvetica',sans-serif" fill="#6C606B" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-3">
    <text x="-93.29" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-2.5</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-2.0</text>
    <text x="-47.72" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-1.5</text>
    <text x="-24.94" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-1.0</text>
    <text x="-2.15" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-0.5</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">0.0</text>
    <text x="43.42" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">0.5</text>
    <text x="66.2" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">1.0</text>
    <text x="88.99" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">1.5</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">2.0</text>
    <text x="134.56" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">2.5</text>
    <text x="157.34" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">3.0</text>
    <text x="180.12" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">3.5</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">4.0</text>
    <text x="225.69" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">4.5</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-2.0</text>
    <text x="-65.95" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.9</text>
    <text x="-61.39" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.8</text>
    <text x="-56.84" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.7</text>
    <text x="-52.28" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.6</text>
    <text x="-47.72" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.5</text>
    <text x="-43.17" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.4</text>
    <text x="-38.61" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.3</text>
    <text x="-34.05" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.2</text>
    <text x="-29.49" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.1</text>
    <text x="-24.94" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.0</text>
    <text x="-20.38" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.9</text>
    <text x="-15.82" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.8</text>
    <text x="-11.27" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.7</text>
    <text x="-6.71" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.6</text>
    <text x="-2.15" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.5</text>
    <text x="2.4" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.4</text>
    <text x="6.96" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.3</text>
    <text x="11.52" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.2</text>
    <text x="16.07" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.1</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.0</text>
    <text x="25.19" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.1</text>
    <text x="29.75" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.2</text>
    <text x="34.3" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.3</text>
    <text x="38.86" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.4</text>
    <text x="43.42" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.5</text>
    <text x="47.97" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.6</text>
    <text x="52.53" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.7</text>
    <text x="57.09" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.8</text>
    <text x="61.64" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.9</text>
    <text x="66.2" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.0</text>
    <text x="70.76" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.1</text>
    <text x="75.31" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.2</text>
    <text x="79.87" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.3</text>
    <text x="84.43" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.4</text>
    <text x="88.99" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.5</text>
    <text x="93.54" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.6</text>
    <text x="98.1" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.7</text>
    <text x="102.66" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.8</text>
    <text x="107.21" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.9</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.0</text>
    <text x="116.33" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.1</text>
    <text x="120.88" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.2</text>
    <text x="125.44" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.3</text>
    <text x="130" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.4</text>
    <text x="134.56" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.5</text>
    <text x="139.11" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.6</text>
    <text x="143.67" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.7</text>
    <text x="148.23" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.8</text>
    <text x="152.78" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.9</text>
    <text x="157.34" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.0</text>
    <text x="161.9" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.1</text>
    <text x="166.45" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.2</text>
    <text x="171.01" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.3</text>
    <text x="175.57" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.4</text>
    <text x="180.12" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.5</text>
    <text x="184.68" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.6</text>
    <text x="189.24" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.7</text>
    <text x="193.8" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.8</text>
    <text x="198.35" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.9</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">4.0</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">-2</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">0</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">2</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">4</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-2.0</text>
    <text x="-61.39" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.8</text>
    <text x="-52.28" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.6</text>
    <text x="-43.17" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.4</text>
    <text x="-34.05" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.2</text>
    <text x="-24.94" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.0</text>
    <text x="-15.82" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.8</text>
    <text x="-6.71" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.6</text>
    <text x="2.4" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.4</text>
    <text x="11.52" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.2</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.0</text>
    <text x="29.75" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.2</text>
    <text x="38.86" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.4</text>
    <text x="47.97" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.6</text>
    <text x="57.09" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.8</text>
    <text x="66.2" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.0</text>
    <text x="75.31" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.2</text>
    <text x="84.43" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.4</text>
    <text x="93.54" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.6</text>
    <text x="102.66" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.8</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.0</text>
    <text x="120.88" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.2</text>
    <text x="130" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.4</text>
    <text x="139.11" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.6</text>
    <text x="148.23" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.8</text>
    <text x="157.34" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.0</text>
    <text x="166.45" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.2</text>
    <text x="175.57" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.4</text>
    <text x="184.68" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.6</text>
    <text x="193.8" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.8</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">4.0</text>
  </g>
  <g class="guide colorkey" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-4">
    <g fill="#4C404B" font-size="2.82" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-5">
      <text x="118.24" y="47.57" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-6" class="color_f1">f<tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">1</tspan><tspan dy="-0.498000em"></tspan></text>
      <text x="118.24" y="52.51" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-7" class="color_f2">f<tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">2</tspan><tspan dy="-0.498000em"></tspan></text>
    </g>
    <g stroke="none" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-8">
      <rect x="114.77" y="46.33" width="2.47" height="2.47" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-9" fill="#00BFFF" class="color_f1"/>
      <rect x="114.77" y="51.27" width="2.47" height="2.47" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-10" fill="#D4CA3A" class="color_f2"/>
    </g>
    <g fill="#362A35" font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" stroke="none" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-11">
      <text x="114.77" y="42.43" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-12">Map Function</text>
    </g>
  </g>
  <g clip-path="url(#fig-371e21ceeb8a4893938846e9321c8d7c-element-14)" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-13">
    <g pointer-events="visible" opacity="1" fill="none" stroke="none" class="guide background" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-15">
      <rect x="18.63" y="14.42" width="95.14" height="66.3" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-16"/>
    </g>
    <g class="guide ygridlines xfixed" stroke-dasharray="0.5,0.5" stroke-width="0.2" stroke="#D0D0E0" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-17">
      <path fill="none" d="M18.63,153.47 L 113.77 153.47" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-18" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-19" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,128.55 L 113.77 128.55" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-20" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,116.09 L 113.77 116.09" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-21" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,103.63 L 113.77 103.63" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-22" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,91.17 L 113.77 91.17" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-23" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-24" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,66.26 L 113.77 66.26" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-25" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,53.8 L 113.77 53.8" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-26" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,41.34 L 113.77 41.34" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-27" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,28.88 L 113.77 28.88" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-28" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-29" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,3.96 L 113.77 3.96" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-30" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-8.5 L 113.77 -8.5" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-31" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-20.96 L 113.77 -20.96" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-32" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-33.42 L 113.77 -33.42" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-33" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-34" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-58.34 L 113.77 -58.34" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-35" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-36" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,138.52 L 113.77 138.52" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-37" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,136.03 L 113.77 136.03" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-38" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,133.54 L 113.77 133.54" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-39" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,131.04 L 113.77 131.04" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-40" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,128.55 L 113.77 128.55" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-41" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,126.06 L 113.77 126.06" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-42" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,123.57 L 113.77 123.57" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-43" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,121.08 L 113.77 121.08" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-44" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,118.59 L 113.77 118.59" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-45" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,116.09 L 113.77 116.09" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-46" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,113.6 L 113.77 113.6" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-47" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,111.11 L 113.77 111.11" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-48" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,108.62 L 113.77 108.62" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-49" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,106.13 L 113.77 106.13" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-50" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,103.63 L 113.77 103.63" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-51" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,101.14 L 113.77 101.14" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-52" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,98.65 L 113.77 98.65" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-53" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,96.16 L 113.77 96.16" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-54" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,93.67 L 113.77 93.67" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-55" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,91.17 L 113.77 91.17" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-56" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,88.68 L 113.77 88.68" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-57" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,86.19 L 113.77 86.19" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-58" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,83.7 L 113.77 83.7" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-59" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,81.21 L 113.77 81.21" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-60" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-61" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,76.22 L 113.77 76.22" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-62" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,73.73 L 113.77 73.73" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-63" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,71.24 L 113.77 71.24" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-64" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,68.75 L 113.77 68.75" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-65" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,66.26 L 113.77 66.26" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-66" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,63.76 L 113.77 63.76" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-67" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,61.27 L 113.77 61.27" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-68" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,58.78 L 113.77 58.78" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-69" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,56.29 L 113.77 56.29" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-70" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,53.8 L 113.77 53.8" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-71" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,51.3 L 113.77 51.3" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-72" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,48.81 L 113.77 48.81" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-73" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,46.32 L 113.77 46.32" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-74" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,43.83 L 113.77 43.83" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-75" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,41.34 L 113.77 41.34" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-76" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,38.84 L 113.77 38.84" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-77" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,36.35 L 113.77 36.35" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-78" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,33.86 L 113.77 33.86" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-79" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,31.37 L 113.77 31.37" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-80" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,28.88 L 113.77 28.88" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-81" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,26.39 L 113.77 26.39" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-82" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,23.89 L 113.77 23.89" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-83" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,21.4 L 113.77 21.4" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-84" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,18.91 L 113.77 18.91" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-85" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-86" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,13.93 L 113.77 13.93" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-87" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,11.43 L 113.77 11.43" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-88" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,8.94 L 113.77 8.94" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-89" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,6.45 L 113.77 6.45" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-90" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,3.96 L 113.77 3.96" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-91" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,1.47 L 113.77 1.47" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-92" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-1.03 L 113.77 -1.03" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-93" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-3.52 L 113.77 -3.52" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-94" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-6.01 L 113.77 -6.01" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-95" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-8.5 L 113.77 -8.5" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-96" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-10.99 L 113.77 -10.99" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-97" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-13.49 L 113.77 -13.49" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-98" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-15.98 L 113.77 -15.98" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-99" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-18.47 L 113.77 -18.47" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-100" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-20.96 L 113.77 -20.96" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-101" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-23.45 L 113.77 -23.45" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-102" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-25.94 L 113.77 -25.94" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-103" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-28.44 L 113.77 -28.44" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-104" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-30.93 L 113.77 -30.93" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-105" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-33.42 L 113.77 -33.42" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-106" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-35.91 L 113.77 -35.91" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-107" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-38.4 L 113.77 -38.4" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-108" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-40.9 L 113.77 -40.9" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-109" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-43.39 L 113.77 -43.39" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-110" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-111" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-112" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-113" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-114" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-115" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-116" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,134.78 L 113.77 134.78" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-117" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,128.55 L 113.77 128.55" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-118" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,122.32 L 113.77 122.32" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-119" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,116.09 L 113.77 116.09" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-120" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,109.86 L 113.77 109.86" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-121" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,103.63 L 113.77 103.63" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-122" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,97.4 L 113.77 97.4" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-123" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,91.17 L 113.77 91.17" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-124" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,84.94 L 113.77 84.94" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-125" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-126" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,72.49 L 113.77 72.49" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-127" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,66.26 L 113.77 66.26" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-128" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,60.03 L 113.77 60.03" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-129" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,53.8 L 113.77 53.8" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-130" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,47.57 L 113.77 47.57" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-131" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,41.34 L 113.77 41.34" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-132" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,35.11 L 113.77 35.11" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-133" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,28.88 L 113.77 28.88" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-134" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,22.65 L 113.77 22.65" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-135" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-136" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,10.19 L 113.77 10.19" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-137" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,3.96 L 113.77 3.96" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-138" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-2.27 L 113.77 -2.27" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-139" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-8.5 L 113.77 -8.5" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-140" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-14.73 L 113.77 -14.73" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-141" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-20.96 L 113.77 -20.96" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-142" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-27.19 L 113.77 -27.19" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-143" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-33.42 L 113.77 -33.42" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-144" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-39.65 L 113.77 -39.65" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-145" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-146" gadfly:scale="5.0" visibility="hidden"/>
    </g>
    <g class="guide xgridlines yfixed" stroke-dasharray="0.5,0.5" stroke-width="0.2" stroke="#D0D0E0" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-147">
      <path fill="none" d="M-93.29,14.42 L -93.29 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-148" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-149" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-47.72,14.42 L -47.72 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-150" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-24.94,14.42 L -24.94 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-151" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-2.15,14.42 L -2.15 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-152" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-153" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M43.42,14.42 L 43.42 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-154" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M66.2,14.42 L 66.2 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-155" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M88.99,14.42 L 88.99 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-156" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-157" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M134.56,14.42 L 134.56 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-158" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M157.34,14.42 L 157.34 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-159" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M180.12,14.42 L 180.12 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-160" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-161" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M225.69,14.42 L 225.69 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-162" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-163" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-65.95,14.42 L -65.95 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-164" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-61.39,14.42 L -61.39 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-165" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-56.84,14.42 L -56.84 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-166" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-52.28,14.42 L -52.28 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-167" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-47.72,14.42 L -47.72 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-168" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-43.17,14.42 L -43.17 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-169" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-38.61,14.42 L -38.61 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-170" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-34.05,14.42 L -34.05 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-171" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-29.49,14.42 L -29.49 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-172" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-24.94,14.42 L -24.94 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-173" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-20.38,14.42 L -20.38 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-174" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-15.82,14.42 L -15.82 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-175" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-11.27,14.42 L -11.27 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-176" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-6.71,14.42 L -6.71 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-177" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-2.15,14.42 L -2.15 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-178" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M2.4,14.42 L 2.4 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-179" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M6.96,14.42 L 6.96 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-180" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M11.52,14.42 L 11.52 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-181" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M16.07,14.42 L 16.07 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-182" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-183" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M25.19,14.42 L 25.19 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-184" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M29.75,14.42 L 29.75 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-185" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M34.3,14.42 L 34.3 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-186" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M38.86,14.42 L 38.86 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-187" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M43.42,14.42 L 43.42 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-188" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M47.97,14.42 L 47.97 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-189" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M52.53,14.42 L 52.53 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-190" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M57.09,14.42 L 57.09 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-191" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M61.64,14.42 L 61.64 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-192" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M66.2,14.42 L 66.2 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-193" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M70.76,14.42 L 70.76 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-194" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M75.31,14.42 L 75.31 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-195" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M79.87,14.42 L 79.87 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-196" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M84.43,14.42 L 84.43 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-197" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M88.99,14.42 L 88.99 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-198" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M93.54,14.42 L 93.54 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-199" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M98.1,14.42 L 98.1 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-200" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M102.66,14.42 L 102.66 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-201" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M107.21,14.42 L 107.21 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-202" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-203" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M116.33,14.42 L 116.33 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-204" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M120.88,14.42 L 120.88 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-205" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M125.44,14.42 L 125.44 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-206" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M130,14.42 L 130 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-207" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M134.56,14.42 L 134.56 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-208" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M139.11,14.42 L 139.11 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-209" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M143.67,14.42 L 143.67 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-210" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M148.23,14.42 L 148.23 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-211" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M152.78,14.42 L 152.78 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-212" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M157.34,14.42 L 157.34 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-213" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M161.9,14.42 L 161.9 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-214" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M166.45,14.42 L 166.45 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-215" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M171.01,14.42 L 171.01 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-216" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M175.57,14.42 L 175.57 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-217" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M180.12,14.42 L 180.12 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-218" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M184.68,14.42 L 184.68 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-219" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M189.24,14.42 L 189.24 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-220" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M193.8,14.42 L 193.8 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-221" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M198.35,14.42 L 198.35 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-222" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-223" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-224" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-225" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-226" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-227" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-228" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-61.39,14.42 L -61.39 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-229" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-52.28,14.42 L -52.28 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-230" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-43.17,14.42 L -43.17 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-231" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-34.05,14.42 L -34.05 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-232" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-24.94,14.42 L -24.94 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-233" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-15.82,14.42 L -15.82 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-234" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-6.71,14.42 L -6.71 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-235" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M2.4,14.42 L 2.4 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-236" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M11.52,14.42 L 11.52 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-237" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-238" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M29.75,14.42 L 29.75 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-239" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M38.86,14.42 L 38.86 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-240" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M47.97,14.42 L 47.97 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-241" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M57.09,14.42 L 57.09 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-242" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M66.2,14.42 L 66.2 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-243" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M75.31,14.42 L 75.31 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-244" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M84.43,14.42 L 84.43 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-245" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M93.54,14.42 L 93.54 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-246" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M102.66,14.42 L 102.66 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-247" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-248" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M120.88,14.42 L 120.88 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-249" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M130,14.42 L 130 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-250" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M139.11,14.42 L 139.11 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-251" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M148.23,14.42 L 148.23 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-252" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M157.34,14.42 L 157.34 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-253" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M166.45,14.42 L 166.45 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-254" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M175.57,14.42 L 175.57 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-255" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M184.68,14.42 L 184.68 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-256" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M193.8,14.42 L 193.8 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-257" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-258" gadfly:scale="5.0" visibility="hidden"/>
    </g>
    <g class="plotpanel" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-259">
      <g stroke-width="0.3" fill="none" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-260">
        <path fill="none" d="M20.63,78.72 L 21 77.72 21.36 76.75 21.73 75.78 22.1 74.84 22.46 73.91 22.83 72.99 23.19 72.09 23.56 71.2 23.93 70.33 24.29 69.47 24.66 68.62 25.02 67.79 25.39 66.97 25.76 66.17 26.12 65.38 26.49 64.6 26.85 63.83 27.22 63.07 27.59 62.33 27.95 61.6 28.32 60.88 28.68 60.17 29.05 59.47 29.42 58.78 29.78 58.11 30.15 57.45 30.51 56.79 30.88 56.15 31.25 55.51 31.61 54.89 31.98 54.28 32.34 53.68 32.71 53.08 33.08 52.5 33.44 51.92 33.81 51.36 34.17 50.8 34.54 50.25 34.91 49.71 35.27 49.18 35.64 48.66 36 48.15 36.37 47.64 36.74 47.14 37.1 46.65 37.47 46.17 37.83 45.7 38.2 45.23 38.57 44.77 38.93 44.32 39.3 43.88 39.66 43.44 40.03 43.01 40.4 42.58 40.76 42.17 41.13 41.76 41.49 41.35 41.86 40.95 42.23 40.56 42.59 40.18 42.96 39.8 43.32 39.43 43.69 39.06 44.06 38.7 44.42 38.35 44.79 38 45.15 37.65 45.52 37.31 45.89 36.98 46.25 36.65 46.62 36.33 46.99 36.01 47.35 35.7 47.72 35.39 48.08 35.09 48.45 34.79 48.82 34.5 49.18 34.21 49.55 33.93 49.91 33.65 50.28 33.38 50.65 33.1 51.01 32.84 51.38 32.58 51.74 32.32 52.11 32.07 52.48 31.82 52.84 31.57 53.21 31.33 53.57 31.09 53.94 30.86 54.31 30.63 54.67 30.4 55.04 30.18 55.4 29.96 55.77 29.74 56.14 29.53 56.5 29.32 56.87 29.12 57.23 28.91 57.6 28.72 57.97 28.52 58.33 28.33 58.7 28.14 59.06 27.95 59.43 27.77 59.8 27.59 60.16 27.41 60.53 27.23 60.89 27.06 61.26 26.89 61.63 26.72 61.99 26.56 62.36 26.4 62.72 26.24 63.09 26.08 63.46 25.93 63.82 25.78 64.19 25.63 64.55 25.48 64.92 25.34 65.29 25.19 65.65 25.05 66.02 24.92 66.38 24.78 66.75 24.65 67.12 24.52 67.48 24.39 67.85 24.26 68.21 24.14 68.58 24.01 68.95 23.89 69.31 23.77 69.68 23.66 70.04 23.54 70.41 23.43 70.78 23.31 71.14 23.2 71.51 23.1 71.87 22.99 72.24 22.89 72.61 22.78 72.97 22.68 73.34 22.58 73.7 22.48 74.07 22.39 74.44 22.29 74.8 22.2 75.17 22.11 75.53 22.01 75.9 21.93 76.27 21.84 76.63 21.75 77 21.67 77.36 21.58 77.73 21.5 78.1 21.42 78.46 21.34 78.83 21.26 79.19 21.18 79.56 21.11 79.93 21.03 80.29 20.96 80.66 20.89 81.02 20.82 81.39 20.75 81.76 20.68 82.12 20.61 82.49 20.54 82.85 20.48 83.22 20.41 83.59 20.35 83.95 20.29 84.32 20.22 84.69 20.16 85.05 20.1 85.42 20.05 85.78 19.99 86.15 19.93 86.52 19.87 86.88 19.82 87.25 19.77 87.61 19.71 87.98 19.66 88.35 19.61 88.71 19.56 89.08 19.51 89.44 19.46 89.81 19.41 90.18 19.36 90.54 19.31 90.91 19.27 91.27 19.22 91.64 19.18 92.01 19.13 92.37 19.09 92.74 19.05 93.1 19.01 93.47 18.97 93.84 18.92 94.2 18.88 94.57 18.85 94.93 18.81 95.3 18.77 95.67 18.73 96.03 18.69 96.4 18.66 96.76 18.62 97.13 18.59 97.5 18.55 97.86 18.52 98.23 18.48 98.59 18.45 98.96 18.42 99.33 18.39 99.69 18.36 100.06 18.33 100.42 18.29 100.79 18.27 101.16 18.24 101.52 18.21 101.89 18.18 102.25 18.15 102.62 18.12 102.99 18.1 103.35 18.07 103.72 18.04 104.08 18.02 104.45 17.99 104.82 17.97 105.18 17.94 105.55 17.92 105.91 17.89 106.28 17.87 106.65 17.85 107.01 17.82 107.38 17.8 107.74 17.78 108.11 17.76 108.48 17.74 108.84 17.71 109.21 17.69 109.57 17.67 109.94 17.65 110.31 17.63 110.67 17.61 111.04 17.6 111.4 17.58 111.77 17.56" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-261" stroke="#D4CA3A" class="geometry color_f2"/>
        <path fill="none" d="M20.63,78.72 L 21 77.72 21.36 76.74 21.73 75.77 22.1 74.82 22.46 73.88 22.83 72.95 23.19 72.03 23.56 71.13 23.93 70.23 24.29 69.35 24.66 68.49 25.02 67.63 25.39 66.79 25.76 65.95 26.12 65.13 26.49 64.32 26.85 63.52 27.22 62.74 27.59 61.96 27.95 61.2 28.32 60.44 28.68 59.7 29.05 58.96 29.42 58.24 29.78 57.53 30.15 56.82 30.51 56.13 30.88 55.45 31.25 54.78 31.61 54.11 31.98 53.46 32.34 52.81 32.71 52.18 33.08 51.55 33.44 50.94 33.81 50.33 34.17 49.73 34.54 49.14 34.91 48.56 35.27 47.99 35.64 47.43 36 46.87 36.37 46.32 36.74 45.78 37.1 45.25 37.47 44.73 37.83 44.22 38.2 43.71 38.57 43.21 38.93 42.72 39.3 42.23 39.66 41.76 40.03 41.29 40.4 40.83 40.76 40.37 41.13 39.92 41.49 39.48 41.86 39.05 42.23 38.62 42.59 38.2 42.96 37.79 43.32 37.38 43.69 36.98 44.06 36.59 44.42 36.2 44.79 35.82 45.15 35.44 45.52 35.07 45.89 34.71 46.25 34.35 46.62 34 46.99 33.65 47.35 33.31 47.72 32.98 48.08 32.65 48.45 32.33 48.82 32.01 49.18 31.7 49.55 31.39 49.91 31.09 50.28 30.79 50.65 30.5 51.01 30.21 51.38 29.93 51.74 29.65 52.11 29.38 52.48 29.11 52.84 28.84 53.21 28.59 53.57 28.33 53.94 28.08 54.31 27.84 54.67 27.59 55.04 27.36 55.4 27.12 55.77 26.9 56.14 26.67 56.5 26.45 56.87 26.23 57.23 26.02 57.6 25.81 57.97 25.61 58.33 25.41 58.7 25.21 59.06 25.02 59.43 24.83 59.8 24.64 60.16 24.45 60.53 24.27 60.89 24.1 61.26 23.93 61.63 23.76 61.99 23.59 62.36 23.42 62.72 23.26 63.09 23.11 63.46 22.95 63.82 22.8 64.19 22.65 64.55 22.51 64.92 22.36 65.29 22.22 65.65 22.09 66.02 21.95 66.38 21.82 66.75 21.69 67.12 21.57 67.48 21.44 67.85 21.32 68.21 21.2 68.58 21.08 68.95 20.97 69.31 20.86 69.68 20.75 70.04 20.64 70.41 20.54 70.78 20.43 71.14 20.33 71.51 20.23 71.87 20.14 72.24 20.04 72.61 19.95 72.97 19.86 73.34 19.77 73.7 19.68 74.07 19.6 74.44 19.52 74.8 19.43 75.17 19.36 75.53 19.28 75.9 19.2 76.27 19.13 76.63 19.05 77 18.98 77.36 18.91 77.73 18.85 78.1 18.78 78.46 18.72 78.83 18.65 79.19 18.59 79.56 18.53 79.93 18.47 80.29 18.41 80.66 18.36 81.02 18.3 81.39 18.25 81.76 18.2 82.12 18.15 82.49 18.1 82.85 18.05 83.22 18 83.59 17.95 83.95 17.91 84.32 17.86 84.69 17.82 85.05 17.78 85.42 17.74 85.78 17.7 86.15 17.66 86.52 17.62 86.88 17.59 87.25 17.55 87.61 17.51 87.98 17.48 88.35 17.45 88.71 17.41 89.08 17.38 89.44 17.35 89.81 17.32 90.18 17.29 90.54 17.27 90.91 17.24 91.27 17.21 91.64 17.19 92.01 17.16 92.37 17.14 92.74 17.11 93.1 17.09 93.47 17.07 93.84 17.04 94.2 17.02 94.57 17 94.93 16.98 95.3 16.96 95.67 16.94 96.03 16.92 96.4 16.91 96.76 16.89 97.13 16.87 97.5 16.86 97.86 16.84 98.23 16.82 98.59 16.81 98.96 16.8 99.33 16.78 99.69 16.77 100.06 16.75 100.42 16.74 100.79 16.73 101.16 16.72 101.52 16.71 101.89 16.69 102.25 16.68 102.62 16.67 102.99 16.66 103.35 16.65 103.72 16.64 104.08 16.64 104.45 16.63 104.82 16.62 105.18 16.61 105.55 16.6 105.91 16.59 106.28 16.59 106.65 16.58 107.01 16.57 107.38 16.57 107.74 16.56 108.11 16.55 108.48 16.55 108.84 16.54 109.21 16.54 109.57 16.53 109.94 16.53 110.31 16.52 110.67 16.52 111.04 16.51 111.4 16.51 111.77 16.5" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-262" stroke="#00BFFF" class="geometry color_f1"/>
      </g>
    </g>
    <g opacity="0" class="guide zoomslider" stroke="none" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-263">
      <g fill="#EAEAEA" stroke-width="0.3" stroke-opacity="0" stroke="#6A6A6A" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-264">
        <rect x="106.77" y="17.42" width="4" height="4" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-265"/>
        <g class="button_logo" fill="#6A6A6A" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-266">
          <path d="M107.57,19.02 L 108.37 19.02 108.37 18.22 109.17 18.22 109.17 19.02 109.97 19.02 109.97 19.82 109.17 19.82 109.17 20.62 108.37 20.62 108.37 19.82 107.57 19.82 z" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-267"/>
        </g>
      </g>
      <g fill="#EAEAEA" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-268">
        <rect x="87.27" y="17.42" width="19" height="4" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-269"/>
      </g>
      <g class="zoomslider_thumb" fill="#6A6A6A" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-270">
        <rect x="95.77" y="17.42" width="2" height="4" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-271"/>
      </g>
      <g fill="#EAEAEA" stroke-width="0.3" stroke-opacity="0" stroke="#6A6A6A" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-272">
        <rect x="82.77" y="17.42" width="4" height="4" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-273"/>
        <g class="button_logo" fill="#6A6A6A" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-274">
          <path d="M83.57,19.02 L 85.97 19.02 85.97 19.82 83.57 19.82 z" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-275"/>
        </g>
      </g>
    </g>
  </g>
  <g class="guide ylabels" font-size="2.82" font-family="'PT Sans Caption','Helvetica Neue','Helvetica',sans-serif" fill="#6C606B" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-276">
    <text x="17.63" y="153.47" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-277" gadfly:scale="1.0" visibility="hidden">-0.6</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-278" gadfly:scale="1.0" visibility="hidden">-0.5</text>
    <text x="17.63" y="128.55" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-279" gadfly:scale="1.0" visibility="hidden">-0.4</text>
    <text x="17.63" y="116.09" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-280" gadfly:scale="1.0" visibility="hidden">-0.3</text>
    <text x="17.63" y="103.63" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-281" gadfly:scale="1.0" visibility="hidden">-0.2</text>
    <text x="17.63" y="91.17" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-282" gadfly:scale="1.0" visibility="hidden">-0.1</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-283" gadfly:scale="1.0" visibility="visible">0.0</text>
    <text x="17.63" y="66.26" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-284" gadfly:scale="1.0" visibility="visible">0.1</text>
    <text x="17.63" y="53.8" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-285" gadfly:scale="1.0" visibility="visible">0.2</text>
    <text x="17.63" y="41.34" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-286" gadfly:scale="1.0" visibility="visible">0.3</text>
    <text x="17.63" y="28.88" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-287" gadfly:scale="1.0" visibility="visible">0.4</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-288" gadfly:scale="1.0" visibility="visible">0.5</text>
    <text x="17.63" y="3.96" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-289" gadfly:scale="1.0" visibility="hidden">0.6</text>
    <text x="17.63" y="-8.5" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-290" gadfly:scale="1.0" visibility="hidden">0.7</text>
    <text x="17.63" y="-20.96" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-291" gadfly:scale="1.0" visibility="hidden">0.8</text>
    <text x="17.63" y="-33.42" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-292" gadfly:scale="1.0" visibility="hidden">0.9</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-293" gadfly:scale="1.0" visibility="hidden">1.0</text>
    <text x="17.63" y="-58.34" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-294" gadfly:scale="1.0" visibility="hidden">1.1</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-295" gadfly:scale="10.0" visibility="hidden">-0.50</text>
    <text x="17.63" y="138.52" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-296" gadfly:scale="10.0" visibility="hidden">-0.48</text>
    <text x="17.63" y="136.03" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-297" gadfly:scale="10.0" visibility="hidden">-0.46</text>
    <text x="17.63" y="133.54" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-298" gadfly:scale="10.0" visibility="hidden">-0.44</text>
    <text x="17.63" y="131.04" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-299" gadfly:scale="10.0" visibility="hidden">-0.42</text>
    <text x="17.63" y="128.55" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-300" gadfly:scale="10.0" visibility="hidden">-0.40</text>
    <text x="17.63" y="126.06" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-301" gadfly:scale="10.0" visibility="hidden">-0.38</text>
    <text x="17.63" y="123.57" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-302" gadfly:scale="10.0" visibility="hidden">-0.36</text>
    <text x="17.63" y="121.08" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-303" gadfly:scale="10.0" visibility="hidden">-0.34</text>
    <text x="17.63" y="118.59" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-304" gadfly:scale="10.0" visibility="hidden">-0.32</text>
    <text x="17.63" y="116.09" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-305" gadfly:scale="10.0" visibility="hidden">-0.30</text>
    <text x="17.63" y="113.6" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-306" gadfly:scale="10.0" visibility="hidden">-0.28</text>
    <text x="17.63" y="111.11" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-307" gadfly:scale="10.0" visibility="hidden">-0.26</text>
    <text x="17.63" y="108.62" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-308" gadfly:scale="10.0" visibility="hidden">-0.24</text>
    <text x="17.63" y="106.13" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-309" gadfly:scale="10.0" visibility="hidden">-0.22</text>
    <text x="17.63" y="103.63" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-310" gadfly:scale="10.0" visibility="hidden">-0.20</text>
    <text x="17.63" y="101.14" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-311" gadfly:scale="10.0" visibility="hidden">-0.18</text>
    <text x="17.63" y="98.65" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-312" gadfly:scale="10.0" visibility="hidden">-0.16</text>
    <text x="17.63" y="96.16" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-313" gadfly:scale="10.0" visibility="hidden">-0.14</text>
    <text x="17.63" y="93.67" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-314" gadfly:scale="10.0" visibility="hidden">-0.12</text>
    <text x="17.63" y="91.17" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-315" gadfly:scale="10.0" visibility="hidden">-0.10</text>
    <text x="17.63" y="88.68" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-316" gadfly:scale="10.0" visibility="hidden">-0.08</text>
    <text x="17.63" y="86.19" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-317" gadfly:scale="10.0" visibility="hidden">-0.06</text>
    <text x="17.63" y="83.7" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-318" gadfly:scale="10.0" visibility="hidden">-0.04</text>
    <text x="17.63" y="81.21" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-319" gadfly:scale="10.0" visibility="hidden">-0.02</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-320" gadfly:scale="10.0" visibility="hidden">0.00</text>
    <text x="17.63" y="76.22" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-321" gadfly:scale="10.0" visibility="hidden">0.02</text>
    <text x="17.63" y="73.73" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-322" gadfly:scale="10.0" visibility="hidden">0.04</text>
    <text x="17.63" y="71.24" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-323" gadfly:scale="10.0" visibility="hidden">0.06</text>
    <text x="17.63" y="68.75" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-324" gadfly:scale="10.0" visibility="hidden">0.08</text>
    <text x="17.63" y="66.26" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-325" gadfly:scale="10.0" visibility="hidden">0.10</text>
    <text x="17.63" y="63.76" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-326" gadfly:scale="10.0" visibility="hidden">0.12</text>
    <text x="17.63" y="61.27" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-327" gadfly:scale="10.0" visibility="hidden">0.14</text>
    <text x="17.63" y="58.78" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-328" gadfly:scale="10.0" visibility="hidden">0.16</text>
    <text x="17.63" y="56.29" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-329" gadfly:scale="10.0" visibility="hidden">0.18</text>
    <text x="17.63" y="53.8" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-330" gadfly:scale="10.0" visibility="hidden">0.20</text>
    <text x="17.63" y="51.3" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-331" gadfly:scale="10.0" visibility="hidden">0.22</text>
    <text x="17.63" y="48.81" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-332" gadfly:scale="10.0" visibility="hidden">0.24</text>
    <text x="17.63" y="46.32" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-333" gadfly:scale="10.0" visibility="hidden">0.26</text>
    <text x="17.63" y="43.83" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-334" gadfly:scale="10.0" visibility="hidden">0.28</text>
    <text x="17.63" y="41.34" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-335" gadfly:scale="10.0" visibility="hidden">0.30</text>
    <text x="17.63" y="38.84" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-336" gadfly:scale="10.0" visibility="hidden">0.32</text>
    <text x="17.63" y="36.35" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-337" gadfly:scale="10.0" visibility="hidden">0.34</text>
    <text x="17.63" y="33.86" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-338" gadfly:scale="10.0" visibility="hidden">0.36</text>
    <text x="17.63" y="31.37" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-339" gadfly:scale="10.0" visibility="hidden">0.38</text>
    <text x="17.63" y="28.88" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-340" gadfly:scale="10.0" visibility="hidden">0.40</text>
    <text x="17.63" y="26.39" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-341" gadfly:scale="10.0" visibility="hidden">0.42</text>
    <text x="17.63" y="23.89" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-342" gadfly:scale="10.0" visibility="hidden">0.44</text>
    <text x="17.63" y="21.4" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-343" gadfly:scale="10.0" visibility="hidden">0.46</text>
    <text x="17.63" y="18.91" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-344" gadfly:scale="10.0" visibility="hidden">0.48</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-345" gadfly:scale="10.0" visibility="hidden">0.50</text>
    <text x="17.63" y="13.93" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-346" gadfly:scale="10.0" visibility="hidden">0.52</text>
    <text x="17.63" y="11.43" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-347" gadfly:scale="10.0" visibility="hidden">0.54</text>
    <text x="17.63" y="8.94" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-348" gadfly:scale="10.0" visibility="hidden">0.56</text>
    <text x="17.63" y="6.45" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-349" gadfly:scale="10.0" visibility="hidden">0.58</text>
    <text x="17.63" y="3.96" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-350" gadfly:scale="10.0" visibility="hidden">0.60</text>
    <text x="17.63" y="1.47" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-351" gadfly:scale="10.0" visibility="hidden">0.62</text>
    <text x="17.63" y="-1.03" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-352" gadfly:scale="10.0" visibility="hidden">0.64</text>
    <text x="17.63" y="-3.52" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-353" gadfly:scale="10.0" visibility="hidden">0.66</text>
    <text x="17.63" y="-6.01" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-354" gadfly:scale="10.0" visibility="hidden">0.68</text>
    <text x="17.63" y="-8.5" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-355" gadfly:scale="10.0" visibility="hidden">0.70</text>
    <text x="17.63" y="-10.99" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-356" gadfly:scale="10.0" visibility="hidden">0.72</text>
    <text x="17.63" y="-13.49" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-357" gadfly:scale="10.0" visibility="hidden">0.74</text>
    <text x="17.63" y="-15.98" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-358" gadfly:scale="10.0" visibility="hidden">0.76</text>
    <text x="17.63" y="-18.47" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-359" gadfly:scale="10.0" visibility="hidden">0.78</text>
    <text x="17.63" y="-20.96" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-360" gadfly:scale="10.0" visibility="hidden">0.80</text>
    <text x="17.63" y="-23.45" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-361" gadfly:scale="10.0" visibility="hidden">0.82</text>
    <text x="17.63" y="-25.94" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-362" gadfly:scale="10.0" visibility="hidden">0.84</text>
    <text x="17.63" y="-28.44" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-363" gadfly:scale="10.0" visibility="hidden">0.86</text>
    <text x="17.63" y="-30.93" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-364" gadfly:scale="10.0" visibility="hidden">0.88</text>
    <text x="17.63" y="-33.42" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-365" gadfly:scale="10.0" visibility="hidden">0.90</text>
    <text x="17.63" y="-35.91" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-366" gadfly:scale="10.0" visibility="hidden">0.92</text>
    <text x="17.63" y="-38.4" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-367" gadfly:scale="10.0" visibility="hidden">0.94</text>
    <text x="17.63" y="-40.9" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-368" gadfly:scale="10.0" visibility="hidden">0.96</text>
    <text x="17.63" y="-43.39" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-369" gadfly:scale="10.0" visibility="hidden">0.98</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-370" gadfly:scale="10.0" visibility="hidden">1.00</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-371" gadfly:scale="0.5" visibility="hidden">-0.5</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-372" gadfly:scale="0.5" visibility="hidden">0.0</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-373" gadfly:scale="0.5" visibility="hidden">0.5</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-374" gadfly:scale="0.5" visibility="hidden">1.0</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-375" gadfly:scale="5.0" visibility="hidden">-0.50</text>
    <text x="17.63" y="134.78" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-376" gadfly:scale="5.0" visibility="hidden">-0.45</text>
    <text x="17.63" y="128.55" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-377" gadfly:scale="5.0" visibility="hidden">-0.40</text>
    <text x="17.63" y="122.32" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-378" gadfly:scale="5.0" visibility="hidden">-0.35</text>
    <text x="17.63" y="116.09" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-379" gadfly:scale="5.0" visibility="hidden">-0.30</text>
    <text x="17.63" y="109.86" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-380" gadfly:scale="5.0" visibility="hidden">-0.25</text>
    <text x="17.63" y="103.63" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-381" gadfly:scale="5.0" visibility="hidden">-0.20</text>
    <text x="17.63" y="97.4" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-382" gadfly:scale="5.0" visibility="hidden">-0.15</text>
    <text x="17.63" y="91.17" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-383" gadfly:scale="5.0" visibility="hidden">-0.10</text>
    <text x="17.63" y="84.94" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-384" gadfly:scale="5.0" visibility="hidden">-0.05</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-385" gadfly:scale="5.0" visibility="hidden">0.00</text>
    <text x="17.63" y="72.49" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-386" gadfly:scale="5.0" visibility="hidden">0.05</text>
    <text x="17.63" y="66.26" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-387" gadfly:scale="5.0" visibility="hidden">0.10</text>
    <text x="17.63" y="60.03" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-388" gadfly:scale="5.0" visibility="hidden">0.15</text>
    <text x="17.63" y="53.8" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-389" gadfly:scale="5.0" visibility="hidden">0.20</text>
    <text x="17.63" y="47.57" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-390" gadfly:scale="5.0" visibility="hidden">0.25</text>
    <text x="17.63" y="41.34" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-391" gadfly:scale="5.0" visibility="hidden">0.30</text>
    <text x="17.63" y="35.11" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-392" gadfly:scale="5.0" visibility="hidden">0.35</text>
    <text x="17.63" y="28.88" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-393" gadfly:scale="5.0" visibility="hidden">0.40</text>
    <text x="17.63" y="22.65" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-394" gadfly:scale="5.0" visibility="hidden">0.45</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-395" gadfly:scale="5.0" visibility="hidden">0.50</text>
    <text x="17.63" y="10.19" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-396" gadfly:scale="5.0" visibility="hidden">0.55</text>
    <text x="17.63" y="3.96" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-397" gadfly:scale="5.0" visibility="hidden">0.60</text>
    <text x="17.63" y="-2.27" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-398" gadfly:scale="5.0" visibility="hidden">0.65</text>
    <text x="17.63" y="-8.5" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-399" gadfly:scale="5.0" visibility="hidden">0.70</text>
    <text x="17.63" y="-14.73" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-400" gadfly:scale="5.0" visibility="hidden">0.75</text>
    <text x="17.63" y="-20.96" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-401" gadfly:scale="5.0" visibility="hidden">0.80</text>
    <text x="17.63" y="-27.19" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-402" gadfly:scale="5.0" visibility="hidden">0.85</text>
    <text x="17.63" y="-33.42" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-403" gadfly:scale="5.0" visibility="hidden">0.90</text>
    <text x="17.63" y="-39.65" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-404" gadfly:scale="5.0" visibility="hidden">0.95</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-405" gadfly:scale="5.0" visibility="hidden">1.00</text>
  </g>
  <g font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" fill="#564A55" stroke="none" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-406">
    <text x="8.81" y="45.57" text-anchor="middle" dy="0.35em" transform="rotate(-90, 8.81, 47.57)" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-407">Recombination Rate</text>
  </g>
  <g font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" fill="#564A55" stroke="none" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-408">
    <text x="66.2" y="12.42" text-anchor="middle" id="fig-371e21ceeb8a4893938846e9321c8d7c-element-409">Karlin's (f<tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">1</tspan><tspan dy="-0.498000em">) and Haldane's (f</tspan><tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">2</tspan><tspan dy="-0.498000em">) Map Functions</tspan></text>
  </g>
</g>
<defs>
<clipPath id="fig-371e21ceeb8a4893938846e9321c8d7c-element-14">
  <path d="M18.63,14.42 L 113.77 14.42 113.77 80.72 18.63 80.72" />
</clipPath
></defs>
<script> <![CDATA[
(function(N){var k=/[\.\/]/,L=/\s*,\s*/,C=function(a,d){return a-d},a,v,y={n:{}},M=function(){for(var a=0,d=this.length;a<d;a++)if("undefined"!=typeof this[a])return this[a]},A=function(){for(var a=this.length;--a;)if("undefined"!=typeof this[a])return this[a]},w=function(k,d){k=String(k);var f=v,n=Array.prototype.slice.call(arguments,2),u=w.listeners(k),p=0,b,q=[],e={},l=[],r=a;l.firstDefined=M;l.lastDefined=A;a=k;for(var s=v=0,x=u.length;s<x;s++)"zIndex"in u[s]&&(q.push(u[s].zIndex),0>u[s].zIndex&&
(e[u[s].zIndex]=u[s]));for(q.sort(C);0>q[p];)if(b=e[q[p++] ],l.push(b.apply(d,n)),v)return v=f,l;for(s=0;s<x;s++)if(b=u[s],"zIndex"in b)if(b.zIndex==q[p]){l.push(b.apply(d,n));if(v)break;do if(p++,(b=e[q[p] ])&&l.push(b.apply(d,n)),v)break;while(b)}else e[b.zIndex]=b;else if(l.push(b.apply(d,n)),v)break;v=f;a=r;return l};w._events=y;w.listeners=function(a){a=a.split(k);var d=y,f,n,u,p,b,q,e,l=[d],r=[];u=0;for(p=a.length;u<p;u++){e=[];b=0;for(q=l.length;b<q;b++)for(d=l[b].n,f=[d[a[u] ],d["*"] ],n=2;n--;)if(d=
f[n])e.push(d),r=r.concat(d.f||[]);l=e}return r};w.on=function(a,d){a=String(a);if("function"!=typeof d)return function(){};for(var f=a.split(L),n=0,u=f.length;n<u;n++)(function(a){a=a.split(k);for(var b=y,f,e=0,l=a.length;e<l;e++)b=b.n,b=b.hasOwnProperty(a[e])&&b[a[e] ]||(b[a[e] ]={n:{}});b.f=b.f||[];e=0;for(l=b.f.length;e<l;e++)if(b.f[e]==d){f=!0;break}!f&&b.f.push(d)})(f[n]);return function(a){+a==+a&&(d.zIndex=+a)}};w.f=function(a){var d=[].slice.call(arguments,1);return function(){w.apply(null,
[a,null].concat(d).concat([].slice.call(arguments,0)))}};w.stop=function(){v=1};w.nt=function(k){return k?(new RegExp("(?:\\.|\\/|^)"+k+"(?:\\.|\\/|$)")).test(a):a};w.nts=function(){return a.split(k)};w.off=w.unbind=function(a,d){if(a){var f=a.split(L);if(1<f.length)for(var n=0,u=f.length;n<u;n++)w.off(f[n],d);else{for(var f=a.split(k),p,b,q,e,l=[y],n=0,u=f.length;n<u;n++)for(e=0;e<l.length;e+=q.length-2){q=[e,1];p=l[e].n;if("*"!=f[n])p[f[n] ]&&q.push(p[f[n] ]);else for(b in p)p.hasOwnProperty(b)&&
q.push(p[b]);l.splice.apply(l,q)}n=0;for(u=l.length;n<u;n++)for(p=l[n];p.n;){if(d){if(p.f){e=0;for(f=p.f.length;e<f;e++)if(p.f[e]==d){p.f.splice(e,1);break}!p.f.length&&delete p.f}for(b in p.n)if(p.n.hasOwnProperty(b)&&p.n[b].f){q=p.n[b].f;e=0;for(f=q.length;e<f;e++)if(q[e]==d){q.splice(e,1);break}!q.length&&delete p.n[b].f}}else for(b in delete p.f,p.n)p.n.hasOwnProperty(b)&&p.n[b].f&&delete p.n[b].f;p=p.n}}}else w._events=y={n:{}}};w.once=function(a,d){var f=function(){w.unbind(a,f);return d.apply(this,
arguments)};return w.on(a,f)};w.version="0.4.2";w.toString=function(){return"You are running Eve 0.4.2"};"undefined"!=typeof module&&module.exports?module.exports=w:"function"===typeof define&&define.amd?define("eve",[],function(){return w}):N.eve=w})(this);
(function(N,k){"function"===typeof define&&define.amd?define("Snap.svg",["eve"],function(L){return k(N,L)}):k(N,N.eve)})(this,function(N,k){var L=function(a){var k={},y=N.requestAnimationFrame||N.webkitRequestAnimationFrame||N.mozRequestAnimationFrame||N.oRequestAnimationFrame||N.msRequestAnimationFrame||function(a){setTimeout(a,16)},M=Array.isArray||function(a){return a instanceof Array||"[object Array]"==Object.prototype.toString.call(a)},A=0,w="M"+(+new Date).toString(36),z=function(a){if(null==
a)return this.s;var b=this.s-a;this.b+=this.dur*b;this.B+=this.dur*b;this.s=a},d=function(a){if(null==a)return this.spd;this.spd=a},f=function(a){if(null==a)return this.dur;this.s=this.s*a/this.dur;this.dur=a},n=function(){delete k[this.id];this.update();a("mina.stop."+this.id,this)},u=function(){this.pdif||(delete k[this.id],this.update(),this.pdif=this.get()-this.b)},p=function(){this.pdif&&(this.b=this.get()-this.pdif,delete this.pdif,k[this.id]=this)},b=function(){var a;if(M(this.start)){a=[];
for(var b=0,e=this.start.length;b<e;b++)a[b]=+this.start[b]+(this.end[b]-this.start[b])*this.easing(this.s)}else a=+this.start+(this.end-this.start)*this.easing(this.s);this.set(a)},q=function(){var l=0,b;for(b in k)if(k.hasOwnProperty(b)){var e=k[b],f=e.get();l++;e.s=(f-e.b)/(e.dur/e.spd);1<=e.s&&(delete k[b],e.s=1,l--,function(b){setTimeout(function(){a("mina.finish."+b.id,b)})}(e));e.update()}l&&y(q)},e=function(a,r,s,x,G,h,J){a={id:w+(A++).toString(36),start:a,end:r,b:s,s:0,dur:x-s,spd:1,get:G,
set:h,easing:J||e.linear,status:z,speed:d,duration:f,stop:n,pause:u,resume:p,update:b};k[a.id]=a;r=0;for(var K in k)if(k.hasOwnProperty(K)&&(r++,2==r))break;1==r&&y(q);return a};e.time=Date.now||function(){return+new Date};e.getById=function(a){return k[a]||null};e.linear=function(a){return a};e.easeout=function(a){return Math.pow(a,1.7)};e.easein=function(a){return Math.pow(a,0.48)};e.easeinout=function(a){if(1==a)return 1;if(0==a)return 0;var b=0.48-a/1.04,e=Math.sqrt(0.1734+b*b);a=e-b;a=Math.pow(Math.abs(a),
1/3)*(0>a?-1:1);b=-e-b;b=Math.pow(Math.abs(b),1/3)*(0>b?-1:1);a=a+b+0.5;return 3*(1-a)*a*a+a*a*a};e.backin=function(a){return 1==a?1:a*a*(2.70158*a-1.70158)};e.backout=function(a){if(0==a)return 0;a-=1;return a*a*(2.70158*a+1.70158)+1};e.elastic=function(a){return a==!!a?a:Math.pow(2,-10*a)*Math.sin(2*(a-0.075)*Math.PI/0.3)+1};e.bounce=function(a){a<1/2.75?a*=7.5625*a:a<2/2.75?(a-=1.5/2.75,a=7.5625*a*a+0.75):a<2.5/2.75?(a-=2.25/2.75,a=7.5625*a*a+0.9375):(a-=2.625/2.75,a=7.5625*a*a+0.984375);return a};
return N.mina=e}("undefined"==typeof k?function(){}:k),C=function(){function a(c,t){if(c){if(c.tagName)return x(c);if(y(c,"array")&&a.set)return a.set.apply(a,c);if(c instanceof e)return c;if(null==t)return c=G.doc.querySelector(c),x(c)}return new s(null==c?"100%":c,null==t?"100%":t)}function v(c,a){if(a){"#text"==c&&(c=G.doc.createTextNode(a.text||""));"string"==typeof c&&(c=v(c));if("string"==typeof a)return"xlink:"==a.substring(0,6)?c.getAttributeNS(m,a.substring(6)):"xml:"==a.substring(0,4)?c.getAttributeNS(la,
a.substring(4)):c.getAttribute(a);for(var da in a)if(a[h](da)){var b=J(a[da]);b?"xlink:"==da.substring(0,6)?c.setAttributeNS(m,da.substring(6),b):"xml:"==da.substring(0,4)?c.setAttributeNS(la,da.substring(4),b):c.setAttribute(da,b):c.removeAttribute(da)}}else c=G.doc.createElementNS(la,c);return c}function y(c,a){a=J.prototype.toLowerCase.call(a);return"finite"==a?isFinite(c):"array"==a&&(c instanceof Array||Array.isArray&&Array.isArray(c))?!0:"null"==a&&null===c||a==typeof c&&null!==c||"object"==
a&&c===Object(c)||$.call(c).slice(8,-1).toLowerCase()==a}function M(c){if("function"==typeof c||Object(c)!==c)return c;var a=new c.constructor,b;for(b in c)c[h](b)&&(a[b]=M(c[b]));return a}function A(c,a,b){function m(){var e=Array.prototype.slice.call(arguments,0),f=e.join("\u2400"),d=m.cache=m.cache||{},l=m.count=m.count||[];if(d[h](f)){a:for(var e=l,l=f,B=0,H=e.length;B<H;B++)if(e[B]===l){e.push(e.splice(B,1)[0]);break a}return b?b(d[f]):d[f]}1E3<=l.length&&delete d[l.shift()];l.push(f);d[f]=c.apply(a,
e);return b?b(d[f]):d[f]}return m}function w(c,a,b,m,e,f){return null==e?(c-=b,a-=m,c||a?(180*I.atan2(-a,-c)/C+540)%360:0):w(c,a,e,f)-w(b,m,e,f)}function z(c){return c%360*C/180}function d(c){var a=[];c=c.replace(/(?:^|\s)(\w+)\(([^)]+)\)/g,function(c,b,m){m=m.split(/\s*,\s*|\s+/);"rotate"==b&&1==m.length&&m.push(0,0);"scale"==b&&(2<m.length?m=m.slice(0,2):2==m.length&&m.push(0,0),1==m.length&&m.push(m[0],0,0));"skewX"==b?a.push(["m",1,0,I.tan(z(m[0])),1,0,0]):"skewY"==b?a.push(["m",1,I.tan(z(m[0])),
0,1,0,0]):a.push([b.charAt(0)].concat(m));return c});return a}function f(c,t){var b=O(c),m=new a.Matrix;if(b)for(var e=0,f=b.length;e<f;e++){var h=b[e],d=h.length,B=J(h[0]).toLowerCase(),H=h[0]!=B,l=H?m.invert():0,E;"t"==B&&2==d?m.translate(h[1],0):"t"==B&&3==d?H?(d=l.x(0,0),B=l.y(0,0),H=l.x(h[1],h[2]),l=l.y(h[1],h[2]),m.translate(H-d,l-B)):m.translate(h[1],h[2]):"r"==B?2==d?(E=E||t,m.rotate(h[1],E.x+E.width/2,E.y+E.height/2)):4==d&&(H?(H=l.x(h[2],h[3]),l=l.y(h[2],h[3]),m.rotate(h[1],H,l)):m.rotate(h[1],
h[2],h[3])):"s"==B?2==d||3==d?(E=E||t,m.scale(h[1],h[d-1],E.x+E.width/2,E.y+E.height/2)):4==d?H?(H=l.x(h[2],h[3]),l=l.y(h[2],h[3]),m.scale(h[1],h[1],H,l)):m.scale(h[1],h[1],h[2],h[3]):5==d&&(H?(H=l.x(h[3],h[4]),l=l.y(h[3],h[4]),m.scale(h[1],h[2],H,l)):m.scale(h[1],h[2],h[3],h[4])):"m"==B&&7==d&&m.add(h[1],h[2],h[3],h[4],h[5],h[6])}return m}function n(c,t){if(null==t){var m=!0;t="linearGradient"==c.type||"radialGradient"==c.type?c.node.getAttribute("gradientTransform"):"pattern"==c.type?c.node.getAttribute("patternTransform"):
c.node.getAttribute("transform");if(!t)return new a.Matrix;t=d(t)}else t=a._.rgTransform.test(t)?J(t).replace(/\.{3}|\u2026/g,c._.transform||aa):d(t),y(t,"array")&&(t=a.path?a.path.toString.call(t):J(t)),c._.transform=t;var b=f(t,c.getBBox(1));if(m)return b;c.matrix=b}function u(c){c=c.node.ownerSVGElement&&x(c.node.ownerSVGElement)||c.node.parentNode&&x(c.node.parentNode)||a.select("svg")||a(0,0);var t=c.select("defs"),t=null==t?!1:t.node;t||(t=r("defs",c.node).node);return t}function p(c){return c.node.ownerSVGElement&&
x(c.node.ownerSVGElement)||a.select("svg")}function b(c,a,m){function b(c){if(null==c)return aa;if(c==+c)return c;v(B,{width:c});try{return B.getBBox().width}catch(a){return 0}}function h(c){if(null==c)return aa;if(c==+c)return c;v(B,{height:c});try{return B.getBBox().height}catch(a){return 0}}function e(b,B){null==a?d[b]=B(c.attr(b)||0):b==a&&(d=B(null==m?c.attr(b)||0:m))}var f=p(c).node,d={},B=f.querySelector(".svg---mgr");B||(B=v("rect"),v(B,{x:-9E9,y:-9E9,width:10,height:10,"class":"svg---mgr",
fill:"none"}),f.appendChild(B));switch(c.type){case "rect":e("rx",b),e("ry",h);case "image":e("width",b),e("height",h);case "text":e("x",b);e("y",h);break;case "circle":e("cx",b);e("cy",h);e("r",b);break;case "ellipse":e("cx",b);e("cy",h);e("rx",b);e("ry",h);break;case "line":e("x1",b);e("x2",b);e("y1",h);e("y2",h);break;case "marker":e("refX",b);e("markerWidth",b);e("refY",h);e("markerHeight",h);break;case "radialGradient":e("fx",b);e("fy",h);break;case "tspan":e("dx",b);e("dy",h);break;default:e(a,
b)}f.removeChild(B);return d}function q(c){y(c,"array")||(c=Array.prototype.slice.call(arguments,0));for(var a=0,b=0,m=this.node;this[a];)delete this[a++];for(a=0;a<c.length;a++)"set"==c[a].type?c[a].forEach(function(c){m.appendChild(c.node)}):m.appendChild(c[a].node);for(var h=m.childNodes,a=0;a<h.length;a++)this[b++]=x(h[a]);return this}function e(c){if(c.snap in E)return E[c.snap];var a=this.id=V(),b;try{b=c.ownerSVGElement}catch(m){}this.node=c;b&&(this.paper=new s(b));this.type=c.tagName;this.anims=
{};this._={transform:[]};c.snap=a;E[a]=this;"g"==this.type&&(this.add=q);if(this.type in{g:1,mask:1,pattern:1})for(var e in s.prototype)s.prototype[h](e)&&(this[e]=s.prototype[e])}function l(c){this.node=c}function r(c,a){var b=v(c);a.appendChild(b);return x(b)}function s(c,a){var b,m,f,d=s.prototype;if(c&&"svg"==c.tagName){if(c.snap in E)return E[c.snap];var l=c.ownerDocument;b=new e(c);m=c.getElementsByTagName("desc")[0];f=c.getElementsByTagName("defs")[0];m||(m=v("desc"),m.appendChild(l.createTextNode("Created with Snap")),
b.node.appendChild(m));f||(f=v("defs"),b.node.appendChild(f));b.defs=f;for(var ca in d)d[h](ca)&&(b[ca]=d[ca]);b.paper=b.root=b}else b=r("svg",G.doc.body),v(b.node,{height:a,version:1.1,width:c,xmlns:la});return b}function x(c){return!c||c instanceof e||c instanceof l?c:c.tagName&&"svg"==c.tagName.toLowerCase()?new s(c):c.tagName&&"object"==c.tagName.toLowerCase()&&"image/svg+xml"==c.type?new s(c.contentDocument.getElementsByTagName("svg")[0]):new e(c)}a.version="0.3.0";a.toString=function(){return"Snap v"+
this.version};a._={};var G={win:N,doc:N.document};a._.glob=G;var h="hasOwnProperty",J=String,K=parseFloat,U=parseInt,I=Math,P=I.max,Q=I.min,Y=I.abs,C=I.PI,aa="",$=Object.prototype.toString,F=/^\s*((#[a-f\d]{6})|(#[a-f\d]{3})|rgba?\(\s*([\d\.]+%?\s*,\s*[\d\.]+%?\s*,\s*[\d\.]+%?(?:\s*,\s*[\d\.]+%?)?)\s*\)|hsba?\(\s*([\d\.]+(?:deg|\xb0|%)?\s*,\s*[\d\.]+%?\s*,\s*[\d\.]+(?:%?\s*,\s*[\d\.]+)?%?)\s*\)|hsla?\(\s*([\d\.]+(?:deg|\xb0|%)?\s*,\s*[\d\.]+%?\s*,\s*[\d\.]+(?:%?\s*,\s*[\d\.]+)?%?)\s*\))\s*$/i;a._.separator=
RegExp("[,\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]+");var S=RegExp("[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*"),X={hs:1,rg:1},W=RegExp("([a-z])[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029,]*((-?\\d*\\.?\\d*(?:e[\\-+]?\\d+)?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*)+)",
"ig"),ma=RegExp("([rstm])[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029,]*((-?\\d*\\.?\\d*(?:e[\\-+]?\\d+)?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*)+)","ig"),Z=RegExp("(-?\\d*\\.?\\d*(?:e[\\-+]?\\d+)?)[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*",
"ig"),na=0,ba="S"+(+new Date).toString(36),V=function(){return ba+(na++).toString(36)},m="http://www.w3.org/1999/xlink",la="http://www.w3.org/2000/svg",E={},ca=a.url=function(c){return"url('#"+c+"')"};a._.$=v;a._.id=V;a.format=function(){var c=/\{([^\}]+)\}/g,a=/(?:(?:^|\.)(.+?)(?=\[|\.|$|\()|\[('|")(.+?)\2\])(\(\))?/g,b=function(c,b,m){var h=m;b.replace(a,function(c,a,b,m,t){a=a||m;h&&(a in h&&(h=h[a]),"function"==typeof h&&t&&(h=h()))});return h=(null==h||h==m?c:h)+""};return function(a,m){return J(a).replace(c,
function(c,a){return b(c,a,m)})}}();a._.clone=M;a._.cacher=A;a.rad=z;a.deg=function(c){return 180*c/C%360};a.angle=w;a.is=y;a.snapTo=function(c,a,b){b=y(b,"finite")?b:10;if(y(c,"array"))for(var m=c.length;m--;){if(Y(c[m]-a)<=b)return c[m]}else{c=+c;m=a%c;if(m<b)return a-m;if(m>c-b)return a-m+c}return a};a.getRGB=A(function(c){if(!c||(c=J(c)).indexOf("-")+1)return{r:-1,g:-1,b:-1,hex:"none",error:1,toString:ka};if("none"==c)return{r:-1,g:-1,b:-1,hex:"none",toString:ka};!X[h](c.toLowerCase().substring(0,
2))&&"#"!=c.charAt()&&(c=T(c));if(!c)return{r:-1,g:-1,b:-1,hex:"none",error:1,toString:ka};var b,m,e,f,d;if(c=c.match(F)){c[2]&&(e=U(c[2].substring(5),16),m=U(c[2].substring(3,5),16),b=U(c[2].substring(1,3),16));c[3]&&(e=U((d=c[3].charAt(3))+d,16),m=U((d=c[3].charAt(2))+d,16),b=U((d=c[3].charAt(1))+d,16));c[4]&&(d=c[4].split(S),b=K(d[0]),"%"==d[0].slice(-1)&&(b*=2.55),m=K(d[1]),"%"==d[1].slice(-1)&&(m*=2.55),e=K(d[2]),"%"==d[2].slice(-1)&&(e*=2.55),"rgba"==c[1].toLowerCase().slice(0,4)&&(f=K(d[3])),
d[3]&&"%"==d[3].slice(-1)&&(f/=100));if(c[5])return d=c[5].split(S),b=K(d[0]),"%"==d[0].slice(-1)&&(b/=100),m=K(d[1]),"%"==d[1].slice(-1)&&(m/=100),e=K(d[2]),"%"==d[2].slice(-1)&&(e/=100),"deg"!=d[0].slice(-3)&&"\u00b0"!=d[0].slice(-1)||(b/=360),"hsba"==c[1].toLowerCase().slice(0,4)&&(f=K(d[3])),d[3]&&"%"==d[3].slice(-1)&&(f/=100),a.hsb2rgb(b,m,e,f);if(c[6])return d=c[6].split(S),b=K(d[0]),"%"==d[0].slice(-1)&&(b/=100),m=K(d[1]),"%"==d[1].slice(-1)&&(m/=100),e=K(d[2]),"%"==d[2].slice(-1)&&(e/=100),
"deg"!=d[0].slice(-3)&&"\u00b0"!=d[0].slice(-1)||(b/=360),"hsla"==c[1].toLowerCase().slice(0,4)&&(f=K(d[3])),d[3]&&"%"==d[3].slice(-1)&&(f/=100),a.hsl2rgb(b,m,e,f);b=Q(I.round(b),255);m=Q(I.round(m),255);e=Q(I.round(e),255);f=Q(P(f,0),1);c={r:b,g:m,b:e,toString:ka};c.hex="#"+(16777216|e|m<<8|b<<16).toString(16).slice(1);c.opacity=y(f,"finite")?f:1;return c}return{r:-1,g:-1,b:-1,hex:"none",error:1,toString:ka}},a);a.hsb=A(function(c,b,m){return a.hsb2rgb(c,b,m).hex});a.hsl=A(function(c,b,m){return a.hsl2rgb(c,
b,m).hex});a.rgb=A(function(c,a,b,m){if(y(m,"finite")){var e=I.round;return"rgba("+[e(c),e(a),e(b),+m.toFixed(2)]+")"}return"#"+(16777216|b|a<<8|c<<16).toString(16).slice(1)});var T=function(c){var a=G.doc.getElementsByTagName("head")[0]||G.doc.getElementsByTagName("svg")[0];T=A(function(c){if("red"==c.toLowerCase())return"rgb(255, 0, 0)";a.style.color="rgb(255, 0, 0)";a.style.color=c;c=G.doc.defaultView.getComputedStyle(a,aa).getPropertyValue("color");return"rgb(255, 0, 0)"==c?null:c});return T(c)},
qa=function(){return"hsb("+[this.h,this.s,this.b]+")"},ra=function(){return"hsl("+[this.h,this.s,this.l]+")"},ka=function(){return 1==this.opacity||null==this.opacity?this.hex:"rgba("+[this.r,this.g,this.b,this.opacity]+")"},D=function(c,b,m){null==b&&y(c,"object")&&"r"in c&&"g"in c&&"b"in c&&(m=c.b,b=c.g,c=c.r);null==b&&y(c,string)&&(m=a.getRGB(c),c=m.r,b=m.g,m=m.b);if(1<c||1<b||1<m)c/=255,b/=255,m/=255;return[c,b,m]},oa=function(c,b,m,e){c=I.round(255*c);b=I.round(255*b);m=I.round(255*m);c={r:c,
g:b,b:m,opacity:y(e,"finite")?e:1,hex:a.rgb(c,b,m),toString:ka};y(e,"finite")&&(c.opacity=e);return c};a.color=function(c){var b;y(c,"object")&&"h"in c&&"s"in c&&"b"in c?(b=a.hsb2rgb(c),c.r=b.r,c.g=b.g,c.b=b.b,c.opacity=1,c.hex=b.hex):y(c,"object")&&"h"in c&&"s"in c&&"l"in c?(b=a.hsl2rgb(c),c.r=b.r,c.g=b.g,c.b=b.b,c.opacity=1,c.hex=b.hex):(y(c,"string")&&(c=a.getRGB(c)),y(c,"object")&&"r"in c&&"g"in c&&"b"in c&&!("error"in c)?(b=a.rgb2hsl(c),c.h=b.h,c.s=b.s,c.l=b.l,b=a.rgb2hsb(c),c.v=b.b):(c={hex:"none"},
c.r=c.g=c.b=c.h=c.s=c.v=c.l=-1,c.error=1));c.toString=ka;return c};a.hsb2rgb=function(c,a,b,m){y(c,"object")&&"h"in c&&"s"in c&&"b"in c&&(b=c.b,a=c.s,c=c.h,m=c.o);var e,h,d;c=360*c%360/60;d=b*a;a=d*(1-Y(c%2-1));b=e=h=b-d;c=~~c;b+=[d,a,0,0,a,d][c];e+=[a,d,d,a,0,0][c];h+=[0,0,a,d,d,a][c];return oa(b,e,h,m)};a.hsl2rgb=function(c,a,b,m){y(c,"object")&&"h"in c&&"s"in c&&"l"in c&&(b=c.l,a=c.s,c=c.h);if(1<c||1<a||1<b)c/=360,a/=100,b/=100;var e,h,d;c=360*c%360/60;d=2*a*(0.5>b?b:1-b);a=d*(1-Y(c%2-1));b=e=
h=b-d/2;c=~~c;b+=[d,a,0,0,a,d][c];e+=[a,d,d,a,0,0][c];h+=[0,0,a,d,d,a][c];return oa(b,e,h,m)};a.rgb2hsb=function(c,a,b){b=D(c,a,b);c=b[0];a=b[1];b=b[2];var m,e;m=P(c,a,b);e=m-Q(c,a,b);c=((0==e?0:m==c?(a-b)/e:m==a?(b-c)/e+2:(c-a)/e+4)+360)%6*60/360;return{h:c,s:0==e?0:e/m,b:m,toString:qa}};a.rgb2hsl=function(c,a,b){b=D(c,a,b);c=b[0];a=b[1];b=b[2];var m,e,h;m=P(c,a,b);e=Q(c,a,b);h=m-e;c=((0==h?0:m==c?(a-b)/h:m==a?(b-c)/h+2:(c-a)/h+4)+360)%6*60/360;m=(m+e)/2;return{h:c,s:0==h?0:0.5>m?h/(2*m):h/(2-2*
m),l:m,toString:ra}};a.parsePathString=function(c){if(!c)return null;var b=a.path(c);if(b.arr)return a.path.clone(b.arr);var m={a:7,c:6,o:2,h:1,l:2,m:2,r:4,q:4,s:4,t:2,v:1,u:3,z:0},e=[];y(c,"array")&&y(c[0],"array")&&(e=a.path.clone(c));e.length||J(c).replace(W,function(c,a,b){var h=[];c=a.toLowerCase();b.replace(Z,function(c,a){a&&h.push(+a)});"m"==c&&2<h.length&&(e.push([a].concat(h.splice(0,2))),c="l",a="m"==a?"l":"L");"o"==c&&1==h.length&&e.push([a,h[0] ]);if("r"==c)e.push([a].concat(h));else for(;h.length>=
m[c]&&(e.push([a].concat(h.splice(0,m[c]))),m[c]););});e.toString=a.path.toString;b.arr=a.path.clone(e);return e};var O=a.parseTransformString=function(c){if(!c)return null;var b=[];y(c,"array")&&y(c[0],"array")&&(b=a.path.clone(c));b.length||J(c).replace(ma,function(c,a,m){var e=[];a.toLowerCase();m.replace(Z,function(c,a){a&&e.push(+a)});b.push([a].concat(e))});b.toString=a.path.toString;return b};a._.svgTransform2string=d;a._.rgTransform=RegExp("^[a-z][\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*-?\\.?\\d",
"i");a._.transform2matrix=f;a._unit2px=b;a._.getSomeDefs=u;a._.getSomeSVG=p;a.select=function(c){return x(G.doc.querySelector(c))};a.selectAll=function(c){c=G.doc.querySelectorAll(c);for(var b=(a.set||Array)(),m=0;m<c.length;m++)b.push(x(c[m]));return b};setInterval(function(){for(var c in E)if(E[h](c)){var a=E[c],b=a.node;("svg"!=a.type&&!b.ownerSVGElement||"svg"==a.type&&(!b.parentNode||"ownerSVGElement"in b.parentNode&&!b.ownerSVGElement))&&delete E[c]}},1E4);(function(c){function m(c){function a(c,
b){var m=v(c.node,b);(m=(m=m&&m.match(d))&&m[2])&&"#"==m.charAt()&&(m=m.substring(1))&&(f[m]=(f[m]||[]).concat(function(a){var m={};m[b]=ca(a);v(c.node,m)}))}function b(c){var a=v(c.node,"xlink:href");a&&"#"==a.charAt()&&(a=a.substring(1))&&(f[a]=(f[a]||[]).concat(function(a){c.attr("xlink:href","#"+a)}))}var e=c.selectAll("*"),h,d=/^\s*url\(("|'|)(.*)\1\)\s*$/;c=[];for(var f={},l=0,E=e.length;l<E;l++){h=e[l];a(h,"fill");a(h,"stroke");a(h,"filter");a(h,"mask");a(h,"clip-path");b(h);var t=v(h.node,
"id");t&&(v(h.node,{id:h.id}),c.push({old:t,id:h.id}))}l=0;for(E=c.length;l<E;l++)if(e=f[c[l].old])for(h=0,t=e.length;h<t;h++)e[h](c[l].id)}function e(c,a,b){return function(m){m=m.slice(c,a);1==m.length&&(m=m[0]);return b?b(m):m}}function d(c){return function(){var a=c?"<"+this.type:"",b=this.node.attributes,m=this.node.childNodes;if(c)for(var e=0,h=b.length;e<h;e++)a+=" "+b[e].name+'="'+b[e].value.replace(/"/g,'\\"')+'"';if(m.length){c&&(a+=">");e=0;for(h=m.length;e<h;e++)3==m[e].nodeType?a+=m[e].nodeValue:
1==m[e].nodeType&&(a+=x(m[e]).toString());c&&(a+="</"+this.type+">")}else c&&(a+="/>");return a}}c.attr=function(c,a){if(!c)return this;if(y(c,"string"))if(1<arguments.length){var b={};b[c]=a;c=b}else return k("snap.util.getattr."+c,this).firstDefined();for(var m in c)c[h](m)&&k("snap.util.attr."+m,this,c[m]);return this};c.getBBox=function(c){if(!a.Matrix||!a.path)return this.node.getBBox();var b=this,m=new a.Matrix;if(b.removed)return a._.box();for(;"use"==b.type;)if(c||(m=m.add(b.transform().localMatrix.translate(b.attr("x")||
0,b.attr("y")||0))),b.original)b=b.original;else var e=b.attr("xlink:href"),b=b.original=b.node.ownerDocument.getElementById(e.substring(e.indexOf("#")+1));var e=b._,h=a.path.get[b.type]||a.path.get.deflt;try{if(c)return e.bboxwt=h?a.path.getBBox(b.realPath=h(b)):a._.box(b.node.getBBox()),a._.box(e.bboxwt);b.realPath=h(b);b.matrix=b.transform().localMatrix;e.bbox=a.path.getBBox(a.path.map(b.realPath,m.add(b.matrix)));return a._.box(e.bbox)}catch(d){return a._.box()}};var f=function(){return this.string};
c.transform=function(c){var b=this._;if(null==c){var m=this;c=new a.Matrix(this.node.getCTM());for(var e=n(this),h=[e],d=new a.Matrix,l=e.toTransformString(),b=J(e)==J(this.matrix)?J(b.transform):l;"svg"!=m.type&&(m=m.parent());)h.push(n(m));for(m=h.length;m--;)d.add(h[m]);return{string:b,globalMatrix:c,totalMatrix:d,localMatrix:e,diffMatrix:c.clone().add(e.invert()),global:c.toTransformString(),total:d.toTransformString(),local:l,toString:f}}c instanceof a.Matrix?this.matrix=c:n(this,c);this.node&&
("linearGradient"==this.type||"radialGradient"==this.type?v(this.node,{gradientTransform:this.matrix}):"pattern"==this.type?v(this.node,{patternTransform:this.matrix}):v(this.node,{transform:this.matrix}));return this};c.parent=function(){return x(this.node.parentNode)};c.append=c.add=function(c){if(c){if("set"==c.type){var a=this;c.forEach(function(c){a.add(c)});return this}c=x(c);this.node.appendChild(c.node);c.paper=this.paper}return this};c.appendTo=function(c){c&&(c=x(c),c.append(this));return this};
c.prepend=function(c){if(c){if("set"==c.type){var a=this,b;c.forEach(function(c){b?b.after(c):a.prepend(c);b=c});return this}c=x(c);var m=c.parent();this.node.insertBefore(c.node,this.node.firstChild);this.add&&this.add();c.paper=this.paper;this.parent()&&this.parent().add();m&&m.add()}return this};c.prependTo=function(c){c=x(c);c.prepend(this);return this};c.before=function(c){if("set"==c.type){var a=this;c.forEach(function(c){var b=c.parent();a.node.parentNode.insertBefore(c.node,a.node);b&&b.add()});
this.parent().add();return this}c=x(c);var b=c.parent();this.node.parentNode.insertBefore(c.node,this.node);this.parent()&&this.parent().add();b&&b.add();c.paper=this.paper;return this};c.after=function(c){c=x(c);var a=c.parent();this.node.nextSibling?this.node.parentNode.insertBefore(c.node,this.node.nextSibling):this.node.parentNode.appendChild(c.node);this.parent()&&this.parent().add();a&&a.add();c.paper=this.paper;return this};c.insertBefore=function(c){c=x(c);var a=this.parent();c.node.parentNode.insertBefore(this.node,
c.node);this.paper=c.paper;a&&a.add();c.parent()&&c.parent().add();return this};c.insertAfter=function(c){c=x(c);var a=this.parent();c.node.parentNode.insertBefore(this.node,c.node.nextSibling);this.paper=c.paper;a&&a.add();c.parent()&&c.parent().add();return this};c.remove=function(){var c=this.parent();this.node.parentNode&&this.node.parentNode.removeChild(this.node);delete this.paper;this.removed=!0;c&&c.add();return this};c.select=function(c){return x(this.node.querySelector(c))};c.selectAll=
function(c){c=this.node.querySelectorAll(c);for(var b=(a.set||Array)(),m=0;m<c.length;m++)b.push(x(c[m]));return b};c.asPX=function(c,a){null==a&&(a=this.attr(c));return+b(this,c,a)};c.use=function(){var c,a=this.node.id;a||(a=this.id,v(this.node,{id:a}));c="linearGradient"==this.type||"radialGradient"==this.type||"pattern"==this.type?r(this.type,this.node.parentNode):r("use",this.node.parentNode);v(c.node,{"xlink:href":"#"+a});c.original=this;return c};var l=/\S+/g;c.addClass=function(c){var a=(c||
"").match(l)||[];c=this.node;var b=c.className.baseVal,m=b.match(l)||[],e,h,d;if(a.length){for(e=0;d=a[e++];)h=m.indexOf(d),~h||m.push(d);a=m.join(" ");b!=a&&(c.className.baseVal=a)}return this};c.removeClass=function(c){var a=(c||"").match(l)||[];c=this.node;var b=c.className.baseVal,m=b.match(l)||[],e,h;if(m.length){for(e=0;h=a[e++];)h=m.indexOf(h),~h&&m.splice(h,1);a=m.join(" ");b!=a&&(c.className.baseVal=a)}return this};c.hasClass=function(c){return!!~(this.node.className.baseVal.match(l)||[]).indexOf(c)};
c.toggleClass=function(c,a){if(null!=a)return a?this.addClass(c):this.removeClass(c);var b=(c||"").match(l)||[],m=this.node,e=m.className.baseVal,h=e.match(l)||[],d,f,E;for(d=0;E=b[d++];)f=h.indexOf(E),~f?h.splice(f,1):h.push(E);b=h.join(" ");e!=b&&(m.className.baseVal=b);return this};c.clone=function(){var c=x(this.node.cloneNode(!0));v(c.node,"id")&&v(c.node,{id:c.id});m(c);c.insertAfter(this);return c};c.toDefs=function(){u(this).appendChild(this.node);return this};c.pattern=c.toPattern=function(c,
a,b,m){var e=r("pattern",u(this));null==c&&(c=this.getBBox());y(c,"object")&&"x"in c&&(a=c.y,b=c.width,m=c.height,c=c.x);v(e.node,{x:c,y:a,width:b,height:m,patternUnits:"userSpaceOnUse",id:e.id,viewBox:[c,a,b,m].join(" ")});e.node.appendChild(this.node);return e};c.marker=function(c,a,b,m,e,h){var d=r("marker",u(this));null==c&&(c=this.getBBox());y(c,"object")&&"x"in c&&(a=c.y,b=c.width,m=c.height,e=c.refX||c.cx,h=c.refY||c.cy,c=c.x);v(d.node,{viewBox:[c,a,b,m].join(" "),markerWidth:b,markerHeight:m,
orient:"auto",refX:e||0,refY:h||0,id:d.id});d.node.appendChild(this.node);return d};var E=function(c,a,b,m){"function"!=typeof b||b.length||(m=b,b=L.linear);this.attr=c;this.dur=a;b&&(this.easing=b);m&&(this.callback=m)};a._.Animation=E;a.animation=function(c,a,b,m){return new E(c,a,b,m)};c.inAnim=function(){var c=[],a;for(a in this.anims)this.anims[h](a)&&function(a){c.push({anim:new E(a._attrs,a.dur,a.easing,a._callback),mina:a,curStatus:a.status(),status:function(c){return a.status(c)},stop:function(){a.stop()}})}(this.anims[a]);
return c};a.animate=function(c,a,b,m,e,h){"function"!=typeof e||e.length||(h=e,e=L.linear);var d=L.time();c=L(c,a,d,d+m,L.time,b,e);h&&k.once("mina.finish."+c.id,h);return c};c.stop=function(){for(var c=this.inAnim(),a=0,b=c.length;a<b;a++)c[a].stop();return this};c.animate=function(c,a,b,m){"function"!=typeof b||b.length||(m=b,b=L.linear);c instanceof E&&(m=c.callback,b=c.easing,a=b.dur,c=c.attr);var d=[],f=[],l={},t,ca,n,T=this,q;for(q in c)if(c[h](q)){T.equal?(n=T.equal(q,J(c[q])),t=n.from,ca=
n.to,n=n.f):(t=+T.attr(q),ca=+c[q]);var la=y(t,"array")?t.length:1;l[q]=e(d.length,d.length+la,n);d=d.concat(t);f=f.concat(ca)}t=L.time();var p=L(d,f,t,t+a,L.time,function(c){var a={},b;for(b in l)l[h](b)&&(a[b]=l[b](c));T.attr(a)},b);T.anims[p.id]=p;p._attrs=c;p._callback=m;k("snap.animcreated."+T.id,p);k.once("mina.finish."+p.id,function(){delete T.anims[p.id];m&&m.call(T)});k.once("mina.stop."+p.id,function(){delete T.anims[p.id]});return T};var T={};c.data=function(c,b){var m=T[this.id]=T[this.id]||
{};if(0==arguments.length)return k("snap.data.get."+this.id,this,m,null),m;if(1==arguments.length){if(a.is(c,"object")){for(var e in c)c[h](e)&&this.data(e,c[e]);return this}k("snap.data.get."+this.id,this,m[c],c);return m[c]}m[c]=b;k("snap.data.set."+this.id,this,b,c);return this};c.removeData=function(c){null==c?T[this.id]={}:T[this.id]&&delete T[this.id][c];return this};c.outerSVG=c.toString=d(1);c.innerSVG=d()})(e.prototype);a.parse=function(c){var a=G.doc.createDocumentFragment(),b=!0,m=G.doc.createElement("div");
c=J(c);c.match(/^\s*<\s*svg(?:\s|>)/)||(c="<svg>"+c+"</svg>",b=!1);m.innerHTML=c;if(c=m.getElementsByTagName("svg")[0])if(b)a=c;else for(;c.firstChild;)a.appendChild(c.firstChild);m.innerHTML=aa;return new l(a)};l.prototype.select=e.prototype.select;l.prototype.selectAll=e.prototype.selectAll;a.fragment=function(){for(var c=Array.prototype.slice.call(arguments,0),b=G.doc.createDocumentFragment(),m=0,e=c.length;m<e;m++){var h=c[m];h.node&&h.node.nodeType&&b.appendChild(h.node);h.nodeType&&b.appendChild(h);
"string"==typeof h&&b.appendChild(a.parse(h).node)}return new l(b)};a._.make=r;a._.wrap=x;s.prototype.el=function(c,a){var b=r(c,this.node);a&&b.attr(a);return b};k.on("snap.util.getattr",function(){var c=k.nt(),c=c.substring(c.lastIndexOf(".")+1),a=c.replace(/[A-Z]/g,function(c){return"-"+c.toLowerCase()});return pa[h](a)?this.node.ownerDocument.defaultView.getComputedStyle(this.node,null).getPropertyValue(a):v(this.node,c)});var pa={"alignment-baseline":0,"baseline-shift":0,clip:0,"clip-path":0,
"clip-rule":0,color:0,"color-interpolation":0,"color-interpolation-filters":0,"color-profile":0,"color-rendering":0,cursor:0,direction:0,display:0,"dominant-baseline":0,"enable-background":0,fill:0,"fill-opacity":0,"fill-rule":0,filter:0,"flood-color":0,"flood-opacity":0,font:0,"font-family":0,"font-size":0,"font-size-adjust":0,"font-stretch":0,"font-style":0,"font-variant":0,"font-weight":0,"glyph-orientation-horizontal":0,"glyph-orientation-vertical":0,"image-rendering":0,kerning:0,"letter-spacing":0,
"lighting-color":0,marker:0,"marker-end":0,"marker-mid":0,"marker-start":0,mask:0,opacity:0,overflow:0,"pointer-events":0,"shape-rendering":0,"stop-color":0,"stop-opacity":0,stroke:0,"stroke-dasharray":0,"stroke-dashoffset":0,"stroke-linecap":0,"stroke-linejoin":0,"stroke-miterlimit":0,"stroke-opacity":0,"stroke-width":0,"text-anchor":0,"text-decoration":0,"text-rendering":0,"unicode-bidi":0,visibility:0,"word-spacing":0,"writing-mode":0};k.on("snap.util.attr",function(c){var a=k.nt(),b={},a=a.substring(a.lastIndexOf(".")+
1);b[a]=c;var m=a.replace(/-(\w)/gi,function(c,a){return a.toUpperCase()}),a=a.replace(/[A-Z]/g,function(c){return"-"+c.toLowerCase()});pa[h](a)?this.node.style[m]=null==c?aa:c:v(this.node,b)});a.ajax=function(c,a,b,m){var e=new XMLHttpRequest,h=V();if(e){if(y(a,"function"))m=b,b=a,a=null;else if(y(a,"object")){var d=[],f;for(f in a)a.hasOwnProperty(f)&&d.push(encodeURIComponent(f)+"="+encodeURIComponent(a[f]));a=d.join("&")}e.open(a?"POST":"GET",c,!0);a&&(e.setRequestHeader("X-Requested-With","XMLHttpRequest"),
e.setRequestHeader("Content-type","application/x-www-form-urlencoded"));b&&(k.once("snap.ajax."+h+".0",b),k.once("snap.ajax."+h+".200",b),k.once("snap.ajax."+h+".304",b));e.onreadystatechange=function(){4==e.readyState&&k("snap.ajax."+h+"."+e.status,m,e)};if(4==e.readyState)return e;e.send(a);return e}};a.load=function(c,b,m){a.ajax(c,function(c){c=a.parse(c.responseText);m?b.call(m,c):b(c)})};a.getElementByPoint=function(c,a){var b,m,e=G.doc.elementFromPoint(c,a);if(G.win.opera&&"svg"==e.tagName){b=
e;m=b.getBoundingClientRect();b=b.ownerDocument;var h=b.body,d=b.documentElement;b=m.top+(g.win.pageYOffset||d.scrollTop||h.scrollTop)-(d.clientTop||h.clientTop||0);m=m.left+(g.win.pageXOffset||d.scrollLeft||h.scrollLeft)-(d.clientLeft||h.clientLeft||0);h=e.createSVGRect();h.x=c-m;h.y=a-b;h.width=h.height=1;b=e.getIntersectionList(h,null);b.length&&(e=b[b.length-1])}return e?x(e):null};a.plugin=function(c){c(a,e,s,G,l)};return G.win.Snap=a}();C.plugin(function(a,k,y,M,A){function w(a,d,f,b,q,e){null==
d&&"[object SVGMatrix]"==z.call(a)?(this.a=a.a,this.b=a.b,this.c=a.c,this.d=a.d,this.e=a.e,this.f=a.f):null!=a?(this.a=+a,this.b=+d,this.c=+f,this.d=+b,this.e=+q,this.f=+e):(this.a=1,this.c=this.b=0,this.d=1,this.f=this.e=0)}var z=Object.prototype.toString,d=String,f=Math;(function(n){function k(a){return a[0]*a[0]+a[1]*a[1]}function p(a){var d=f.sqrt(k(a));a[0]&&(a[0]/=d);a[1]&&(a[1]/=d)}n.add=function(a,d,e,f,n,p){var k=[[],[],[] ],u=[[this.a,this.c,this.e],[this.b,this.d,this.f],[0,0,1] ];d=[[a,
e,n],[d,f,p],[0,0,1] ];a&&a instanceof w&&(d=[[a.a,a.c,a.e],[a.b,a.d,a.f],[0,0,1] ]);for(a=0;3>a;a++)for(e=0;3>e;e++){for(f=n=0;3>f;f++)n+=u[a][f]*d[f][e];k[a][e]=n}this.a=k[0][0];this.b=k[1][0];this.c=k[0][1];this.d=k[1][1];this.e=k[0][2];this.f=k[1][2];return this};n.invert=function(){var a=this.a*this.d-this.b*this.c;return new w(this.d/a,-this.b/a,-this.c/a,this.a/a,(this.c*this.f-this.d*this.e)/a,(this.b*this.e-this.a*this.f)/a)};n.clone=function(){return new w(this.a,this.b,this.c,this.d,this.e,
this.f)};n.translate=function(a,d){return this.add(1,0,0,1,a,d)};n.scale=function(a,d,e,f){null==d&&(d=a);(e||f)&&this.add(1,0,0,1,e,f);this.add(a,0,0,d,0,0);(e||f)&&this.add(1,0,0,1,-e,-f);return this};n.rotate=function(b,d,e){b=a.rad(b);d=d||0;e=e||0;var l=+f.cos(b).toFixed(9);b=+f.sin(b).toFixed(9);this.add(l,b,-b,l,d,e);return this.add(1,0,0,1,-d,-e)};n.x=function(a,d){return a*this.a+d*this.c+this.e};n.y=function(a,d){return a*this.b+d*this.d+this.f};n.get=function(a){return+this[d.fromCharCode(97+
a)].toFixed(4)};n.toString=function(){return"matrix("+[this.get(0),this.get(1),this.get(2),this.get(3),this.get(4),this.get(5)].join()+")"};n.offset=function(){return[this.e.toFixed(4),this.f.toFixed(4)]};n.determinant=function(){return this.a*this.d-this.b*this.c};n.split=function(){var b={};b.dx=this.e;b.dy=this.f;var d=[[this.a,this.c],[this.b,this.d] ];b.scalex=f.sqrt(k(d[0]));p(d[0]);b.shear=d[0][0]*d[1][0]+d[0][1]*d[1][1];d[1]=[d[1][0]-d[0][0]*b.shear,d[1][1]-d[0][1]*b.shear];b.scaley=f.sqrt(k(d[1]));
p(d[1]);b.shear/=b.scaley;0>this.determinant()&&(b.scalex=-b.scalex);var e=-d[0][1],d=d[1][1];0>d?(b.rotate=a.deg(f.acos(d)),0>e&&(b.rotate=360-b.rotate)):b.rotate=a.deg(f.asin(e));b.isSimple=!+b.shear.toFixed(9)&&(b.scalex.toFixed(9)==b.scaley.toFixed(9)||!b.rotate);b.isSuperSimple=!+b.shear.toFixed(9)&&b.scalex.toFixed(9)==b.scaley.toFixed(9)&&!b.rotate;b.noRotation=!+b.shear.toFixed(9)&&!b.rotate;return b};n.toTransformString=function(a){a=a||this.split();if(+a.shear.toFixed(9))return"m"+[this.get(0),
this.get(1),this.get(2),this.get(3),this.get(4),this.get(5)];a.scalex=+a.scalex.toFixed(4);a.scaley=+a.scaley.toFixed(4);a.rotate=+a.rotate.toFixed(4);return(a.dx||a.dy?"t"+[+a.dx.toFixed(4),+a.dy.toFixed(4)]:"")+(1!=a.scalex||1!=a.scaley?"s"+[a.scalex,a.scaley,0,0]:"")+(a.rotate?"r"+[+a.rotate.toFixed(4),0,0]:"")}})(w.prototype);a.Matrix=w;a.matrix=function(a,d,f,b,k,e){return new w(a,d,f,b,k,e)}});C.plugin(function(a,v,y,M,A){function w(h){return function(d){k.stop();d instanceof A&&1==d.node.childNodes.length&&
("radialGradient"==d.node.firstChild.tagName||"linearGradient"==d.node.firstChild.tagName||"pattern"==d.node.firstChild.tagName)&&(d=d.node.firstChild,b(this).appendChild(d),d=u(d));if(d instanceof v)if("radialGradient"==d.type||"linearGradient"==d.type||"pattern"==d.type){d.node.id||e(d.node,{id:d.id});var f=l(d.node.id)}else f=d.attr(h);else f=a.color(d),f.error?(f=a(b(this).ownerSVGElement).gradient(d))?(f.node.id||e(f.node,{id:f.id}),f=l(f.node.id)):f=d:f=r(f);d={};d[h]=f;e(this.node,d);this.node.style[h]=
x}}function z(a){k.stop();a==+a&&(a+="px");this.node.style.fontSize=a}function d(a){var b=[];a=a.childNodes;for(var e=0,f=a.length;e<f;e++){var l=a[e];3==l.nodeType&&b.push(l.nodeValue);"tspan"==l.tagName&&(1==l.childNodes.length&&3==l.firstChild.nodeType?b.push(l.firstChild.nodeValue):b.push(d(l)))}return b}function f(){k.stop();return this.node.style.fontSize}var n=a._.make,u=a._.wrap,p=a.is,b=a._.getSomeDefs,q=/^url\(#?([^)]+)\)$/,e=a._.$,l=a.url,r=String,s=a._.separator,x="";k.on("snap.util.attr.mask",
function(a){if(a instanceof v||a instanceof A){k.stop();a instanceof A&&1==a.node.childNodes.length&&(a=a.node.firstChild,b(this).appendChild(a),a=u(a));if("mask"==a.type)var d=a;else d=n("mask",b(this)),d.node.appendChild(a.node);!d.node.id&&e(d.node,{id:d.id});e(this.node,{mask:l(d.id)})}});(function(a){k.on("snap.util.attr.clip",a);k.on("snap.util.attr.clip-path",a);k.on("snap.util.attr.clipPath",a)})(function(a){if(a instanceof v||a instanceof A){k.stop();if("clipPath"==a.type)var d=a;else d=
n("clipPath",b(this)),d.node.appendChild(a.node),!d.node.id&&e(d.node,{id:d.id});e(this.node,{"clip-path":l(d.id)})}});k.on("snap.util.attr.fill",w("fill"));k.on("snap.util.attr.stroke",w("stroke"));var G=/^([lr])(?:\(([^)]*)\))?(.*)$/i;k.on("snap.util.grad.parse",function(a){a=r(a);var b=a.match(G);if(!b)return null;a=b[1];var e=b[2],b=b[3],e=e.split(/\s*,\s*/).map(function(a){return+a==a?+a:a});1==e.length&&0==e[0]&&(e=[]);b=b.split("-");b=b.map(function(a){a=a.split(":");var b={color:a[0]};a[1]&&
(b.offset=parseFloat(a[1]));return b});return{type:a,params:e,stops:b}});k.on("snap.util.attr.d",function(b){k.stop();p(b,"array")&&p(b[0],"array")&&(b=a.path.toString.call(b));b=r(b);b.match(/[ruo]/i)&&(b=a.path.toAbsolute(b));e(this.node,{d:b})})(-1);k.on("snap.util.attr.#text",function(a){k.stop();a=r(a);for(a=M.doc.createTextNode(a);this.node.firstChild;)this.node.removeChild(this.node.firstChild);this.node.appendChild(a)})(-1);k.on("snap.util.attr.path",function(a){k.stop();this.attr({d:a})})(-1);
k.on("snap.util.attr.class",function(a){k.stop();this.node.className.baseVal=a})(-1);k.on("snap.util.attr.viewBox",function(a){a=p(a,"object")&&"x"in a?[a.x,a.y,a.width,a.height].join(" "):p(a,"array")?a.join(" "):a;e(this.node,{viewBox:a});k.stop()})(-1);k.on("snap.util.attr.transform",function(a){this.transform(a);k.stop()})(-1);k.on("snap.util.attr.r",function(a){"rect"==this.type&&(k.stop(),e(this.node,{rx:a,ry:a}))})(-1);k.on("snap.util.attr.textpath",function(a){k.stop();if("text"==this.type){var d,
f;if(!a&&this.textPath){for(a=this.textPath;a.node.firstChild;)this.node.appendChild(a.node.firstChild);a.remove();delete this.textPath}else if(p(a,"string")?(d=b(this),a=u(d.parentNode).path(a),d.appendChild(a.node),d=a.id,a.attr({id:d})):(a=u(a),a instanceof v&&(d=a.attr("id"),d||(d=a.id,a.attr({id:d})))),d)if(a=this.textPath,f=this.node,a)a.attr({"xlink:href":"#"+d});else{for(a=e("textPath",{"xlink:href":"#"+d});f.firstChild;)a.appendChild(f.firstChild);f.appendChild(a);this.textPath=u(a)}}})(-1);
k.on("snap.util.attr.text",function(a){if("text"==this.type){for(var b=this.node,d=function(a){var b=e("tspan");if(p(a,"array"))for(var f=0;f<a.length;f++)b.appendChild(d(a[f]));else b.appendChild(M.doc.createTextNode(a));b.normalize&&b.normalize();return b};b.firstChild;)b.removeChild(b.firstChild);for(a=d(a);a.firstChild;)b.appendChild(a.firstChild)}k.stop()})(-1);k.on("snap.util.attr.fontSize",z)(-1);k.on("snap.util.attr.font-size",z)(-1);k.on("snap.util.getattr.transform",function(){k.stop();
return this.transform()})(-1);k.on("snap.util.getattr.textpath",function(){k.stop();return this.textPath})(-1);(function(){function b(d){return function(){k.stop();var b=M.doc.defaultView.getComputedStyle(this.node,null).getPropertyValue("marker-"+d);return"none"==b?b:a(M.doc.getElementById(b.match(q)[1]))}}function d(a){return function(b){k.stop();var d="marker"+a.charAt(0).toUpperCase()+a.substring(1);if(""==b||!b)this.node.style[d]="none";else if("marker"==b.type){var f=b.node.id;f||e(b.node,{id:b.id});
this.node.style[d]=l(f)}}}k.on("snap.util.getattr.marker-end",b("end"))(-1);k.on("snap.util.getattr.markerEnd",b("end"))(-1);k.on("snap.util.getattr.marker-start",b("start"))(-1);k.on("snap.util.getattr.markerStart",b("start"))(-1);k.on("snap.util.getattr.marker-mid",b("mid"))(-1);k.on("snap.util.getattr.markerMid",b("mid"))(-1);k.on("snap.util.attr.marker-end",d("end"))(-1);k.on("snap.util.attr.markerEnd",d("end"))(-1);k.on("snap.util.attr.marker-start",d("start"))(-1);k.on("snap.util.attr.markerStart",
d("start"))(-1);k.on("snap.util.attr.marker-mid",d("mid"))(-1);k.on("snap.util.attr.markerMid",d("mid"))(-1)})();k.on("snap.util.getattr.r",function(){if("rect"==this.type&&e(this.node,"rx")==e(this.node,"ry"))return k.stop(),e(this.node,"rx")})(-1);k.on("snap.util.getattr.text",function(){if("text"==this.type||"tspan"==this.type){k.stop();var a=d(this.node);return 1==a.length?a[0]:a}})(-1);k.on("snap.util.getattr.#text",function(){return this.node.textContent})(-1);k.on("snap.util.getattr.viewBox",
function(){k.stop();var b=e(this.node,"viewBox");if(b)return b=b.split(s),a._.box(+b[0],+b[1],+b[2],+b[3])})(-1);k.on("snap.util.getattr.points",function(){var a=e(this.node,"points");k.stop();if(a)return a.split(s)})(-1);k.on("snap.util.getattr.path",function(){var a=e(this.node,"d");k.stop();return a})(-1);k.on("snap.util.getattr.class",function(){return this.node.className.baseVal})(-1);k.on("snap.util.getattr.fontSize",f)(-1);k.on("snap.util.getattr.font-size",f)(-1)});C.plugin(function(a,v,y,
M,A){function w(a){return a}function z(a){return function(b){return+b.toFixed(3)+a}}var d={"+":function(a,b){return a+b},"-":function(a,b){return a-b},"/":function(a,b){return a/b},"*":function(a,b){return a*b}},f=String,n=/[a-z]+$/i,u=/^\s*([+\-\/*])\s*=\s*([\d.eE+\-]+)\s*([^\d\s]+)?\s*$/;k.on("snap.util.attr",function(a){if(a=f(a).match(u)){var b=k.nt(),b=b.substring(b.lastIndexOf(".")+1),q=this.attr(b),e={};k.stop();var l=a[3]||"",r=q.match(n),s=d[a[1] ];r&&r==l?a=s(parseFloat(q),+a[2]):(q=this.asPX(b),
a=s(this.asPX(b),this.asPX(b,a[2]+l)));isNaN(q)||isNaN(a)||(e[b]=a,this.attr(e))}})(-10);k.on("snap.util.equal",function(a,b){var q=f(this.attr(a)||""),e=f(b).match(u);if(e){k.stop();var l=e[3]||"",r=q.match(n),s=d[e[1] ];if(r&&r==l)return{from:parseFloat(q),to:s(parseFloat(q),+e[2]),f:z(r)};q=this.asPX(a);return{from:q,to:s(q,this.asPX(a,e[2]+l)),f:w}}})(-10)});C.plugin(function(a,v,y,M,A){var w=y.prototype,z=a.is;w.rect=function(a,d,k,p,b,q){var e;null==q&&(q=b);z(a,"object")&&"[object Object]"==
a?e=a:null!=a&&(e={x:a,y:d,width:k,height:p},null!=b&&(e.rx=b,e.ry=q));return this.el("rect",e)};w.circle=function(a,d,k){var p;z(a,"object")&&"[object Object]"==a?p=a:null!=a&&(p={cx:a,cy:d,r:k});return this.el("circle",p)};var d=function(){function a(){this.parentNode.removeChild(this)}return function(d,k){var p=M.doc.createElement("img"),b=M.doc.body;p.style.cssText="position:absolute;left:-9999em;top:-9999em";p.onload=function(){k.call(p);p.onload=p.onerror=null;b.removeChild(p)};p.onerror=a;
b.appendChild(p);p.src=d}}();w.image=function(f,n,k,p,b){var q=this.el("image");if(z(f,"object")&&"src"in f)q.attr(f);else if(null!=f){var e={"xlink:href":f,preserveAspectRatio:"none"};null!=n&&null!=k&&(e.x=n,e.y=k);null!=p&&null!=b?(e.width=p,e.height=b):d(f,function(){a._.$(q.node,{width:this.offsetWidth,height:this.offsetHeight})});a._.$(q.node,e)}return q};w.ellipse=function(a,d,k,p){var b;z(a,"object")&&"[object Object]"==a?b=a:null!=a&&(b={cx:a,cy:d,rx:k,ry:p});return this.el("ellipse",b)};
w.path=function(a){var d;z(a,"object")&&!z(a,"array")?d=a:a&&(d={d:a});return this.el("path",d)};w.group=w.g=function(a){var d=this.el("g");1==arguments.length&&a&&!a.type?d.attr(a):arguments.length&&d.add(Array.prototype.slice.call(arguments,0));return d};w.svg=function(a,d,k,p,b,q,e,l){var r={};z(a,"object")&&null==d?r=a:(null!=a&&(r.x=a),null!=d&&(r.y=d),null!=k&&(r.width=k),null!=p&&(r.height=p),null!=b&&null!=q&&null!=e&&null!=l&&(r.viewBox=[b,q,e,l]));return this.el("svg",r)};w.mask=function(a){var d=
this.el("mask");1==arguments.length&&a&&!a.type?d.attr(a):arguments.length&&d.add(Array.prototype.slice.call(arguments,0));return d};w.ptrn=function(a,d,k,p,b,q,e,l){if(z(a,"object"))var r=a;else arguments.length?(r={},null!=a&&(r.x=a),null!=d&&(r.y=d),null!=k&&(r.width=k),null!=p&&(r.height=p),null!=b&&null!=q&&null!=e&&null!=l&&(r.viewBox=[b,q,e,l])):r={patternUnits:"userSpaceOnUse"};return this.el("pattern",r)};w.use=function(a){return null!=a?(make("use",this.node),a instanceof v&&(a.attr("id")||
a.attr({id:ID()}),a=a.attr("id")),this.el("use",{"xlink:href":a})):v.prototype.use.call(this)};w.text=function(a,d,k){var p={};z(a,"object")?p=a:null!=a&&(p={x:a,y:d,text:k||""});return this.el("text",p)};w.line=function(a,d,k,p){var b={};z(a,"object")?b=a:null!=a&&(b={x1:a,x2:k,y1:d,y2:p});return this.el("line",b)};w.polyline=function(a){1<arguments.length&&(a=Array.prototype.slice.call(arguments,0));var d={};z(a,"object")&&!z(a,"array")?d=a:null!=a&&(d={points:a});return this.el("polyline",d)};
w.polygon=function(a){1<arguments.length&&(a=Array.prototype.slice.call(arguments,0));var d={};z(a,"object")&&!z(a,"array")?d=a:null!=a&&(d={points:a});return this.el("polygon",d)};(function(){function d(){return this.selectAll("stop")}function n(b,d){var f=e("stop"),k={offset:+d+"%"};b=a.color(b);k["stop-color"]=b.hex;1>b.opacity&&(k["stop-opacity"]=b.opacity);e(f,k);this.node.appendChild(f);return this}function u(){if("linearGradient"==this.type){var b=e(this.node,"x1")||0,d=e(this.node,"x2")||
1,f=e(this.node,"y1")||0,k=e(this.node,"y2")||0;return a._.box(b,f,math.abs(d-b),math.abs(k-f))}b=this.node.r||0;return a._.box((this.node.cx||0.5)-b,(this.node.cy||0.5)-b,2*b,2*b)}function p(a,d){function f(a,b){for(var d=(b-u)/(a-w),e=w;e<a;e++)h[e].offset=+(+u+d*(e-w)).toFixed(2);w=a;u=b}var n=k("snap.util.grad.parse",null,d).firstDefined(),p;if(!n)return null;n.params.unshift(a);p="l"==n.type.toLowerCase()?b.apply(0,n.params):q.apply(0,n.params);n.type!=n.type.toLowerCase()&&e(p.node,{gradientUnits:"userSpaceOnUse"});
var h=n.stops,n=h.length,u=0,w=0;n--;for(var v=0;v<n;v++)"offset"in h[v]&&f(v,h[v].offset);h[n].offset=h[n].offset||100;f(n,h[n].offset);for(v=0;v<=n;v++){var y=h[v];p.addStop(y.color,y.offset)}return p}function b(b,k,p,q,w){b=a._.make("linearGradient",b);b.stops=d;b.addStop=n;b.getBBox=u;null!=k&&e(b.node,{x1:k,y1:p,x2:q,y2:w});return b}function q(b,k,p,q,w,h){b=a._.make("radialGradient",b);b.stops=d;b.addStop=n;b.getBBox=u;null!=k&&e(b.node,{cx:k,cy:p,r:q});null!=w&&null!=h&&e(b.node,{fx:w,fy:h});
return b}var e=a._.$;w.gradient=function(a){return p(this.defs,a)};w.gradientLinear=function(a,d,e,f){return b(this.defs,a,d,e,f)};w.gradientRadial=function(a,b,d,e,f){return q(this.defs,a,b,d,e,f)};w.toString=function(){var b=this.node.ownerDocument,d=b.createDocumentFragment(),b=b.createElement("div"),e=this.node.cloneNode(!0);d.appendChild(b);b.appendChild(e);a._.$(e,{xmlns:"http://www.w3.org/2000/svg"});b=b.innerHTML;d.removeChild(d.firstChild);return b};w.clear=function(){for(var a=this.node.firstChild,
b;a;)b=a.nextSibling,"defs"!=a.tagName?a.parentNode.removeChild(a):w.clear.call({node:a}),a=b}})()});C.plugin(function(a,k,y,M){function A(a){var b=A.ps=A.ps||{};b[a]?b[a].sleep=100:b[a]={sleep:100};setTimeout(function(){for(var d in b)b[L](d)&&d!=a&&(b[d].sleep--,!b[d].sleep&&delete b[d])});return b[a]}function w(a,b,d,e){null==a&&(a=b=d=e=0);null==b&&(b=a.y,d=a.width,e=a.height,a=a.x);return{x:a,y:b,width:d,w:d,height:e,h:e,x2:a+d,y2:b+e,cx:a+d/2,cy:b+e/2,r1:F.min(d,e)/2,r2:F.max(d,e)/2,r0:F.sqrt(d*
d+e*e)/2,path:s(a,b,d,e),vb:[a,b,d,e].join(" ")}}function z(){return this.join(",").replace(N,"$1")}function d(a){a=C(a);a.toString=z;return a}function f(a,b,d,h,f,k,l,n,p){if(null==p)return e(a,b,d,h,f,k,l,n);if(0>p||e(a,b,d,h,f,k,l,n)<p)p=void 0;else{var q=0.5,O=1-q,s;for(s=e(a,b,d,h,f,k,l,n,O);0.01<Z(s-p);)q/=2,O+=(s<p?1:-1)*q,s=e(a,b,d,h,f,k,l,n,O);p=O}return u(a,b,d,h,f,k,l,n,p)}function n(b,d){function e(a){return+(+a).toFixed(3)}return a._.cacher(function(a,h,l){a instanceof k&&(a=a.attr("d"));
a=I(a);for(var n,p,D,q,O="",s={},c=0,t=0,r=a.length;t<r;t++){D=a[t];if("M"==D[0])n=+D[1],p=+D[2];else{q=f(n,p,D[1],D[2],D[3],D[4],D[5],D[6]);if(c+q>h){if(d&&!s.start){n=f(n,p,D[1],D[2],D[3],D[4],D[5],D[6],h-c);O+=["C"+e(n.start.x),e(n.start.y),e(n.m.x),e(n.m.y),e(n.x),e(n.y)];if(l)return O;s.start=O;O=["M"+e(n.x),e(n.y)+"C"+e(n.n.x),e(n.n.y),e(n.end.x),e(n.end.y),e(D[5]),e(D[6])].join();c+=q;n=+D[5];p=+D[6];continue}if(!b&&!d)return n=f(n,p,D[1],D[2],D[3],D[4],D[5],D[6],h-c)}c+=q;n=+D[5];p=+D[6]}O+=
D.shift()+D}s.end=O;return n=b?c:d?s:u(n,p,D[0],D[1],D[2],D[3],D[4],D[5],1)},null,a._.clone)}function u(a,b,d,e,h,f,k,l,n){var p=1-n,q=ma(p,3),s=ma(p,2),c=n*n,t=c*n,r=q*a+3*s*n*d+3*p*n*n*h+t*k,q=q*b+3*s*n*e+3*p*n*n*f+t*l,s=a+2*n*(d-a)+c*(h-2*d+a),t=b+2*n*(e-b)+c*(f-2*e+b),x=d+2*n*(h-d)+c*(k-2*h+d),c=e+2*n*(f-e)+c*(l-2*f+e);a=p*a+n*d;b=p*b+n*e;h=p*h+n*k;f=p*f+n*l;l=90-180*F.atan2(s-x,t-c)/S;return{x:r,y:q,m:{x:s,y:t},n:{x:x,y:c},start:{x:a,y:b},end:{x:h,y:f},alpha:l}}function p(b,d,e,h,f,n,k,l){a.is(b,
"array")||(b=[b,d,e,h,f,n,k,l]);b=U.apply(null,b);return w(b.min.x,b.min.y,b.max.x-b.min.x,b.max.y-b.min.y)}function b(a,b,d){return b>=a.x&&b<=a.x+a.width&&d>=a.y&&d<=a.y+a.height}function q(a,d){a=w(a);d=w(d);return b(d,a.x,a.y)||b(d,a.x2,a.y)||b(d,a.x,a.y2)||b(d,a.x2,a.y2)||b(a,d.x,d.y)||b(a,d.x2,d.y)||b(a,d.x,d.y2)||b(a,d.x2,d.y2)||(a.x<d.x2&&a.x>d.x||d.x<a.x2&&d.x>a.x)&&(a.y<d.y2&&a.y>d.y||d.y<a.y2&&d.y>a.y)}function e(a,b,d,e,h,f,n,k,l){null==l&&(l=1);l=(1<l?1:0>l?0:l)/2;for(var p=[-0.1252,
0.1252,-0.3678,0.3678,-0.5873,0.5873,-0.7699,0.7699,-0.9041,0.9041,-0.9816,0.9816],q=[0.2491,0.2491,0.2335,0.2335,0.2032,0.2032,0.1601,0.1601,0.1069,0.1069,0.0472,0.0472],s=0,c=0;12>c;c++)var t=l*p[c]+l,r=t*(t*(-3*a+9*d-9*h+3*n)+6*a-12*d+6*h)-3*a+3*d,t=t*(t*(-3*b+9*e-9*f+3*k)+6*b-12*e+6*f)-3*b+3*e,s=s+q[c]*F.sqrt(r*r+t*t);return l*s}function l(a,b,d){a=I(a);b=I(b);for(var h,f,l,n,k,s,r,O,x,c,t=d?0:[],w=0,v=a.length;w<v;w++)if(x=a[w],"M"==x[0])h=k=x[1],f=s=x[2];else{"C"==x[0]?(x=[h,f].concat(x.slice(1)),
h=x[6],f=x[7]):(x=[h,f,h,f,k,s,k,s],h=k,f=s);for(var G=0,y=b.length;G<y;G++)if(c=b[G],"M"==c[0])l=r=c[1],n=O=c[2];else{"C"==c[0]?(c=[l,n].concat(c.slice(1)),l=c[6],n=c[7]):(c=[l,n,l,n,r,O,r,O],l=r,n=O);var z;var K=x,B=c;z=d;var H=p(K),J=p(B);if(q(H,J)){for(var H=e.apply(0,K),J=e.apply(0,B),H=~~(H/8),J=~~(J/8),U=[],A=[],F={},M=z?0:[],P=0;P<H+1;P++){var C=u.apply(0,K.concat(P/H));U.push({x:C.x,y:C.y,t:P/H})}for(P=0;P<J+1;P++)C=u.apply(0,B.concat(P/J)),A.push({x:C.x,y:C.y,t:P/J});for(P=0;P<H;P++)for(K=
0;K<J;K++){var Q=U[P],L=U[P+1],B=A[K],C=A[K+1],N=0.001>Z(L.x-Q.x)?"y":"x",S=0.001>Z(C.x-B.x)?"y":"x",R;R=Q.x;var Y=Q.y,V=L.x,ea=L.y,fa=B.x,ga=B.y,ha=C.x,ia=C.y;if(W(R,V)<X(fa,ha)||X(R,V)>W(fa,ha)||W(Y,ea)<X(ga,ia)||X(Y,ea)>W(ga,ia))R=void 0;else{var $=(R*ea-Y*V)*(fa-ha)-(R-V)*(fa*ia-ga*ha),aa=(R*ea-Y*V)*(ga-ia)-(Y-ea)*(fa*ia-ga*ha),ja=(R-V)*(ga-ia)-(Y-ea)*(fa-ha);if(ja){var $=$/ja,aa=aa/ja,ja=+$.toFixed(2),ba=+aa.toFixed(2);R=ja<+X(R,V).toFixed(2)||ja>+W(R,V).toFixed(2)||ja<+X(fa,ha).toFixed(2)||
ja>+W(fa,ha).toFixed(2)||ba<+X(Y,ea).toFixed(2)||ba>+W(Y,ea).toFixed(2)||ba<+X(ga,ia).toFixed(2)||ba>+W(ga,ia).toFixed(2)?void 0:{x:$,y:aa}}else R=void 0}R&&F[R.x.toFixed(4)]!=R.y.toFixed(4)&&(F[R.x.toFixed(4)]=R.y.toFixed(4),Q=Q.t+Z((R[N]-Q[N])/(L[N]-Q[N]))*(L.t-Q.t),B=B.t+Z((R[S]-B[S])/(C[S]-B[S]))*(C.t-B.t),0<=Q&&1>=Q&&0<=B&&1>=B&&(z?M++:M.push({x:R.x,y:R.y,t1:Q,t2:B})))}z=M}else z=z?0:[];if(d)t+=z;else{H=0;for(J=z.length;H<J;H++)z[H].segment1=w,z[H].segment2=G,z[H].bez1=x,z[H].bez2=c;t=t.concat(z)}}}return t}
function r(a){var b=A(a);if(b.bbox)return C(b.bbox);if(!a)return w();a=I(a);for(var d=0,e=0,h=[],f=[],l,n=0,k=a.length;n<k;n++)l=a[n],"M"==l[0]?(d=l[1],e=l[2],h.push(d),f.push(e)):(d=U(d,e,l[1],l[2],l[3],l[4],l[5],l[6]),h=h.concat(d.min.x,d.max.x),f=f.concat(d.min.y,d.max.y),d=l[5],e=l[6]);a=X.apply(0,h);l=X.apply(0,f);h=W.apply(0,h);f=W.apply(0,f);f=w(a,l,h-a,f-l);b.bbox=C(f);return f}function s(a,b,d,e,h){if(h)return[["M",+a+ +h,b],["l",d-2*h,0],["a",h,h,0,0,1,h,h],["l",0,e-2*h],["a",h,h,0,0,1,
-h,h],["l",2*h-d,0],["a",h,h,0,0,1,-h,-h],["l",0,2*h-e],["a",h,h,0,0,1,h,-h],["z"] ];a=[["M",a,b],["l",d,0],["l",0,e],["l",-d,0],["z"] ];a.toString=z;return a}function x(a,b,d,e,h){null==h&&null==e&&(e=d);a=+a;b=+b;d=+d;e=+e;if(null!=h){var f=Math.PI/180,l=a+d*Math.cos(-e*f);a+=d*Math.cos(-h*f);var n=b+d*Math.sin(-e*f);b+=d*Math.sin(-h*f);d=[["M",l,n],["A",d,d,0,+(180<h-e),0,a,b] ]}else d=[["M",a,b],["m",0,-e],["a",d,e,0,1,1,0,2*e],["a",d,e,0,1,1,0,-2*e],["z"] ];d.toString=z;return d}function G(b){var e=
A(b);if(e.abs)return d(e.abs);Q(b,"array")&&Q(b&&b[0],"array")||(b=a.parsePathString(b));if(!b||!b.length)return[["M",0,0] ];var h=[],f=0,l=0,n=0,k=0,p=0;"M"==b[0][0]&&(f=+b[0][1],l=+b[0][2],n=f,k=l,p++,h[0]=["M",f,l]);for(var q=3==b.length&&"M"==b[0][0]&&"R"==b[1][0].toUpperCase()&&"Z"==b[2][0].toUpperCase(),s,r,w=p,c=b.length;w<c;w++){h.push(s=[]);r=b[w];p=r[0];if(p!=p.toUpperCase())switch(s[0]=p.toUpperCase(),s[0]){case "A":s[1]=r[1];s[2]=r[2];s[3]=r[3];s[4]=r[4];s[5]=r[5];s[6]=+r[6]+f;s[7]=+r[7]+
l;break;case "V":s[1]=+r[1]+l;break;case "H":s[1]=+r[1]+f;break;case "R":for(var t=[f,l].concat(r.slice(1)),u=2,v=t.length;u<v;u++)t[u]=+t[u]+f,t[++u]=+t[u]+l;h.pop();h=h.concat(P(t,q));break;case "O":h.pop();t=x(f,l,r[1],r[2]);t.push(t[0]);h=h.concat(t);break;case "U":h.pop();h=h.concat(x(f,l,r[1],r[2],r[3]));s=["U"].concat(h[h.length-1].slice(-2));break;case "M":n=+r[1]+f,k=+r[2]+l;default:for(u=1,v=r.length;u<v;u++)s[u]=+r[u]+(u%2?f:l)}else if("R"==p)t=[f,l].concat(r.slice(1)),h.pop(),h=h.concat(P(t,
q)),s=["R"].concat(r.slice(-2));else if("O"==p)h.pop(),t=x(f,l,r[1],r[2]),t.push(t[0]),h=h.concat(t);else if("U"==p)h.pop(),h=h.concat(x(f,l,r[1],r[2],r[3])),s=["U"].concat(h[h.length-1].slice(-2));else for(t=0,u=r.length;t<u;t++)s[t]=r[t];p=p.toUpperCase();if("O"!=p)switch(s[0]){case "Z":f=+n;l=+k;break;case "H":f=s[1];break;case "V":l=s[1];break;case "M":n=s[s.length-2],k=s[s.length-1];default:f=s[s.length-2],l=s[s.length-1]}}h.toString=z;e.abs=d(h);return h}function h(a,b,d,e){return[a,b,d,e,d,
e]}function J(a,b,d,e,h,f){var l=1/3,n=2/3;return[l*a+n*d,l*b+n*e,l*h+n*d,l*f+n*e,h,f]}function K(b,d,e,h,f,l,n,k,p,s){var r=120*S/180,q=S/180*(+f||0),c=[],t,x=a._.cacher(function(a,b,c){var d=a*F.cos(c)-b*F.sin(c);a=a*F.sin(c)+b*F.cos(c);return{x:d,y:a}});if(s)v=s[0],t=s[1],l=s[2],u=s[3];else{t=x(b,d,-q);b=t.x;d=t.y;t=x(k,p,-q);k=t.x;p=t.y;F.cos(S/180*f);F.sin(S/180*f);t=(b-k)/2;v=(d-p)/2;u=t*t/(e*e)+v*v/(h*h);1<u&&(u=F.sqrt(u),e*=u,h*=u);var u=e*e,w=h*h,u=(l==n?-1:1)*F.sqrt(Z((u*w-u*v*v-w*t*t)/
(u*v*v+w*t*t)));l=u*e*v/h+(b+k)/2;var u=u*-h*t/e+(d+p)/2,v=F.asin(((d-u)/h).toFixed(9));t=F.asin(((p-u)/h).toFixed(9));v=b<l?S-v:v;t=k<l?S-t:t;0>v&&(v=2*S+v);0>t&&(t=2*S+t);n&&v>t&&(v-=2*S);!n&&t>v&&(t-=2*S)}if(Z(t-v)>r){var c=t,w=k,G=p;t=v+r*(n&&t>v?1:-1);k=l+e*F.cos(t);p=u+h*F.sin(t);c=K(k,p,e,h,f,0,n,w,G,[t,c,l,u])}l=t-v;f=F.cos(v);r=F.sin(v);n=F.cos(t);t=F.sin(t);l=F.tan(l/4);e=4/3*e*l;l*=4/3*h;h=[b,d];b=[b+e*r,d-l*f];d=[k+e*t,p-l*n];k=[k,p];b[0]=2*h[0]-b[0];b[1]=2*h[1]-b[1];if(s)return[b,d,k].concat(c);
c=[b,d,k].concat(c).join().split(",");s=[];k=0;for(p=c.length;k<p;k++)s[k]=k%2?x(c[k-1],c[k],q).y:x(c[k],c[k+1],q).x;return s}function U(a,b,d,e,h,f,l,k){for(var n=[],p=[[],[] ],s,r,c,t,q=0;2>q;++q)0==q?(r=6*a-12*d+6*h,s=-3*a+9*d-9*h+3*l,c=3*d-3*a):(r=6*b-12*e+6*f,s=-3*b+9*e-9*f+3*k,c=3*e-3*b),1E-12>Z(s)?1E-12>Z(r)||(s=-c/r,0<s&&1>s&&n.push(s)):(t=r*r-4*c*s,c=F.sqrt(t),0>t||(t=(-r+c)/(2*s),0<t&&1>t&&n.push(t),s=(-r-c)/(2*s),0<s&&1>s&&n.push(s)));for(r=q=n.length;q--;)s=n[q],c=1-s,p[0][q]=c*c*c*a+3*
c*c*s*d+3*c*s*s*h+s*s*s*l,p[1][q]=c*c*c*b+3*c*c*s*e+3*c*s*s*f+s*s*s*k;p[0][r]=a;p[1][r]=b;p[0][r+1]=l;p[1][r+1]=k;p[0].length=p[1].length=r+2;return{min:{x:X.apply(0,p[0]),y:X.apply(0,p[1])},max:{x:W.apply(0,p[0]),y:W.apply(0,p[1])}}}function I(a,b){var e=!b&&A(a);if(!b&&e.curve)return d(e.curve);var f=G(a),l=b&&G(b),n={x:0,y:0,bx:0,by:0,X:0,Y:0,qx:null,qy:null},k={x:0,y:0,bx:0,by:0,X:0,Y:0,qx:null,qy:null},p=function(a,b,c){if(!a)return["C",b.x,b.y,b.x,b.y,b.x,b.y];a[0]in{T:1,Q:1}||(b.qx=b.qy=null);
switch(a[0]){case "M":b.X=a[1];b.Y=a[2];break;case "A":a=["C"].concat(K.apply(0,[b.x,b.y].concat(a.slice(1))));break;case "S":"C"==c||"S"==c?(c=2*b.x-b.bx,b=2*b.y-b.by):(c=b.x,b=b.y);a=["C",c,b].concat(a.slice(1));break;case "T":"Q"==c||"T"==c?(b.qx=2*b.x-b.qx,b.qy=2*b.y-b.qy):(b.qx=b.x,b.qy=b.y);a=["C"].concat(J(b.x,b.y,b.qx,b.qy,a[1],a[2]));break;case "Q":b.qx=a[1];b.qy=a[2];a=["C"].concat(J(b.x,b.y,a[1],a[2],a[3],a[4]));break;case "L":a=["C"].concat(h(b.x,b.y,a[1],a[2]));break;case "H":a=["C"].concat(h(b.x,
b.y,a[1],b.y));break;case "V":a=["C"].concat(h(b.x,b.y,b.x,a[1]));break;case "Z":a=["C"].concat(h(b.x,b.y,b.X,b.Y))}return a},s=function(a,b){if(7<a[b].length){a[b].shift();for(var c=a[b];c.length;)q[b]="A",l&&(u[b]="A"),a.splice(b++,0,["C"].concat(c.splice(0,6)));a.splice(b,1);v=W(f.length,l&&l.length||0)}},r=function(a,b,c,d,e){a&&b&&"M"==a[e][0]&&"M"!=b[e][0]&&(b.splice(e,0,["M",d.x,d.y]),c.bx=0,c.by=0,c.x=a[e][1],c.y=a[e][2],v=W(f.length,l&&l.length||0))},q=[],u=[],c="",t="",x=0,v=W(f.length,
l&&l.length||0);for(;x<v;x++){f[x]&&(c=f[x][0]);"C"!=c&&(q[x]=c,x&&(t=q[x-1]));f[x]=p(f[x],n,t);"A"!=q[x]&&"C"==c&&(q[x]="C");s(f,x);l&&(l[x]&&(c=l[x][0]),"C"!=c&&(u[x]=c,x&&(t=u[x-1])),l[x]=p(l[x],k,t),"A"!=u[x]&&"C"==c&&(u[x]="C"),s(l,x));r(f,l,n,k,x);r(l,f,k,n,x);var w=f[x],z=l&&l[x],y=w.length,U=l&&z.length;n.x=w[y-2];n.y=w[y-1];n.bx=$(w[y-4])||n.x;n.by=$(w[y-3])||n.y;k.bx=l&&($(z[U-4])||k.x);k.by=l&&($(z[U-3])||k.y);k.x=l&&z[U-2];k.y=l&&z[U-1]}l||(e.curve=d(f));return l?[f,l]:f}function P(a,
b){for(var d=[],e=0,h=a.length;h-2*!b>e;e+=2){var f=[{x:+a[e-2],y:+a[e-1]},{x:+a[e],y:+a[e+1]},{x:+a[e+2],y:+a[e+3]},{x:+a[e+4],y:+a[e+5]}];b?e?h-4==e?f[3]={x:+a[0],y:+a[1]}:h-2==e&&(f[2]={x:+a[0],y:+a[1]},f[3]={x:+a[2],y:+a[3]}):f[0]={x:+a[h-2],y:+a[h-1]}:h-4==e?f[3]=f[2]:e||(f[0]={x:+a[e],y:+a[e+1]});d.push(["C",(-f[0].x+6*f[1].x+f[2].x)/6,(-f[0].y+6*f[1].y+f[2].y)/6,(f[1].x+6*f[2].x-f[3].x)/6,(f[1].y+6*f[2].y-f[3].y)/6,f[2].x,f[2].y])}return d}y=k.prototype;var Q=a.is,C=a._.clone,L="hasOwnProperty",
N=/,?([a-z]),?/gi,$=parseFloat,F=Math,S=F.PI,X=F.min,W=F.max,ma=F.pow,Z=F.abs;M=n(1);var na=n(),ba=n(0,1),V=a._unit2px;a.path=A;a.path.getTotalLength=M;a.path.getPointAtLength=na;a.path.getSubpath=function(a,b,d){if(1E-6>this.getTotalLength(a)-d)return ba(a,b).end;a=ba(a,d,1);return b?ba(a,b).end:a};y.getTotalLength=function(){if(this.node.getTotalLength)return this.node.getTotalLength()};y.getPointAtLength=function(a){return na(this.attr("d"),a)};y.getSubpath=function(b,d){return a.path.getSubpath(this.attr("d"),
b,d)};a._.box=w;a.path.findDotsAtSegment=u;a.path.bezierBBox=p;a.path.isPointInsideBBox=b;a.path.isBBoxIntersect=q;a.path.intersection=function(a,b){return l(a,b)};a.path.intersectionNumber=function(a,b){return l(a,b,1)};a.path.isPointInside=function(a,d,e){var h=r(a);return b(h,d,e)&&1==l(a,[["M",d,e],["H",h.x2+10] ],1)%2};a.path.getBBox=r;a.path.get={path:function(a){return a.attr("path")},circle:function(a){a=V(a);return x(a.cx,a.cy,a.r)},ellipse:function(a){a=V(a);return x(a.cx||0,a.cy||0,a.rx,
a.ry)},rect:function(a){a=V(a);return s(a.x||0,a.y||0,a.width,a.height,a.rx,a.ry)},image:function(a){a=V(a);return s(a.x||0,a.y||0,a.width,a.height)},line:function(a){return"M"+[a.attr("x1")||0,a.attr("y1")||0,a.attr("x2"),a.attr("y2")]},polyline:function(a){return"M"+a.attr("points")},polygon:function(a){return"M"+a.attr("points")+"z"},deflt:function(a){a=a.node.getBBox();return s(a.x,a.y,a.width,a.height)}};a.path.toRelative=function(b){var e=A(b),h=String.prototype.toLowerCase;if(e.rel)return d(e.rel);
a.is(b,"array")&&a.is(b&&b[0],"array")||(b=a.parsePathString(b));var f=[],l=0,n=0,k=0,p=0,s=0;"M"==b[0][0]&&(l=b[0][1],n=b[0][2],k=l,p=n,s++,f.push(["M",l,n]));for(var r=b.length;s<r;s++){var q=f[s]=[],x=b[s];if(x[0]!=h.call(x[0]))switch(q[0]=h.call(x[0]),q[0]){case "a":q[1]=x[1];q[2]=x[2];q[3]=x[3];q[4]=x[4];q[5]=x[5];q[6]=+(x[6]-l).toFixed(3);q[7]=+(x[7]-n).toFixed(3);break;case "v":q[1]=+(x[1]-n).toFixed(3);break;case "m":k=x[1],p=x[2];default:for(var c=1,t=x.length;c<t;c++)q[c]=+(x[c]-(c%2?l:
n)).toFixed(3)}else for(f[s]=[],"m"==x[0]&&(k=x[1]+l,p=x[2]+n),q=0,c=x.length;q<c;q++)f[s][q]=x[q];x=f[s].length;switch(f[s][0]){case "z":l=k;n=p;break;case "h":l+=+f[s][x-1];break;case "v":n+=+f[s][x-1];break;default:l+=+f[s][x-2],n+=+f[s][x-1]}}f.toString=z;e.rel=d(f);return f};a.path.toAbsolute=G;a.path.toCubic=I;a.path.map=function(a,b){if(!b)return a;var d,e,h,f,l,n,k;a=I(a);h=0;for(l=a.length;h<l;h++)for(k=a[h],f=1,n=k.length;f<n;f+=2)d=b.x(k[f],k[f+1]),e=b.y(k[f],k[f+1]),k[f]=d,k[f+1]=e;return a};
a.path.toString=z;a.path.clone=d});C.plugin(function(a,v,y,C){var A=Math.max,w=Math.min,z=function(a){this.items=[];this.bindings={};this.length=0;this.type="set";if(a)for(var f=0,n=a.length;f<n;f++)a[f]&&(this[this.items.length]=this.items[this.items.length]=a[f],this.length++)};v=z.prototype;v.push=function(){for(var a,f,n=0,k=arguments.length;n<k;n++)if(a=arguments[n])f=this.items.length,this[f]=this.items[f]=a,this.length++;return this};v.pop=function(){this.length&&delete this[this.length--];
return this.items.pop()};v.forEach=function(a,f){for(var n=0,k=this.items.length;n<k&&!1!==a.call(f,this.items[n],n);n++);return this};v.animate=function(d,f,n,u){"function"!=typeof n||n.length||(u=n,n=L.linear);d instanceof a._.Animation&&(u=d.callback,n=d.easing,f=n.dur,d=d.attr);var p=arguments;if(a.is(d,"array")&&a.is(p[p.length-1],"array"))var b=!0;var q,e=function(){q?this.b=q:q=this.b},l=0,r=u&&function(){l++==this.length&&u.call(this)};return this.forEach(function(a,l){k.once("snap.animcreated."+
a.id,e);b?p[l]&&a.animate.apply(a,p[l]):a.animate(d,f,n,r)})};v.remove=function(){for(;this.length;)this.pop().remove();return this};v.bind=function(a,f,k){var u={};if("function"==typeof f)this.bindings[a]=f;else{var p=k||a;this.bindings[a]=function(a){u[p]=a;f.attr(u)}}return this};v.attr=function(a){var f={},k;for(k in a)if(this.bindings[k])this.bindings[k](a[k]);else f[k]=a[k];a=0;for(k=this.items.length;a<k;a++)this.items[a].attr(f);return this};v.clear=function(){for(;this.length;)this.pop()};
v.splice=function(a,f,k){a=0>a?A(this.length+a,0):a;f=A(0,w(this.length-a,f));var u=[],p=[],b=[],q;for(q=2;q<arguments.length;q++)b.push(arguments[q]);for(q=0;q<f;q++)p.push(this[a+q]);for(;q<this.length-a;q++)u.push(this[a+q]);var e=b.length;for(q=0;q<e+u.length;q++)this.items[a+q]=this[a+q]=q<e?b[q]:u[q-e];for(q=this.items.length=this.length-=f-e;this[q];)delete this[q++];return new z(p)};v.exclude=function(a){for(var f=0,k=this.length;f<k;f++)if(this[f]==a)return this.splice(f,1),!0;return!1};
v.insertAfter=function(a){for(var f=this.items.length;f--;)this.items[f].insertAfter(a);return this};v.getBBox=function(){for(var a=[],f=[],k=[],u=[],p=this.items.length;p--;)if(!this.items[p].removed){var b=this.items[p].getBBox();a.push(b.x);f.push(b.y);k.push(b.x+b.width);u.push(b.y+b.height)}a=w.apply(0,a);f=w.apply(0,f);k=A.apply(0,k);u=A.apply(0,u);return{x:a,y:f,x2:k,y2:u,width:k-a,height:u-f,cx:a+(k-a)/2,cy:f+(u-f)/2}};v.clone=function(a){a=new z;for(var f=0,k=this.items.length;f<k;f++)a.push(this.items[f].clone());
return a};v.toString=function(){return"Snap\u2018s set"};v.type="set";a.set=function(){var a=new z;arguments.length&&a.push.apply(a,Array.prototype.slice.call(arguments,0));return a}});C.plugin(function(a,v,y,C){function A(a){var b=a[0];switch(b.toLowerCase()){case "t":return[b,0,0];case "m":return[b,1,0,0,1,0,0];case "r":return 4==a.length?[b,0,a[2],a[3] ]:[b,0];case "s":return 5==a.length?[b,1,1,a[3],a[4] ]:3==a.length?[b,1,1]:[b,1]}}function w(b,d,f){d=q(d).replace(/\.{3}|\u2026/g,b);b=a.parseTransformString(b)||
[];d=a.parseTransformString(d)||[];for(var k=Math.max(b.length,d.length),p=[],v=[],h=0,w,z,y,I;h<k;h++){y=b[h]||A(d[h]);I=d[h]||A(y);if(y[0]!=I[0]||"r"==y[0].toLowerCase()&&(y[2]!=I[2]||y[3]!=I[3])||"s"==y[0].toLowerCase()&&(y[3]!=I[3]||y[4]!=I[4])){b=a._.transform2matrix(b,f());d=a._.transform2matrix(d,f());p=[["m",b.a,b.b,b.c,b.d,b.e,b.f] ];v=[["m",d.a,d.b,d.c,d.d,d.e,d.f] ];break}p[h]=[];v[h]=[];w=0;for(z=Math.max(y.length,I.length);w<z;w++)w in y&&(p[h][w]=y[w]),w in I&&(v[h][w]=I[w])}return{from:u(p),
to:u(v),f:n(p)}}function z(a){return a}function d(a){return function(b){return+b.toFixed(3)+a}}function f(b){return a.rgb(b[0],b[1],b[2])}function n(a){var b=0,d,f,k,n,h,p,q=[];d=0;for(f=a.length;d<f;d++){h="[";p=['"'+a[d][0]+'"'];k=1;for(n=a[d].length;k<n;k++)p[k]="val["+b++ +"]";h+=p+"]";q[d]=h}return Function("val","return Snap.path.toString.call(["+q+"])")}function u(a){for(var b=[],d=0,f=a.length;d<f;d++)for(var k=1,n=a[d].length;k<n;k++)b.push(a[d][k]);return b}var p={},b=/[a-z]+$/i,q=String;
p.stroke=p.fill="colour";v.prototype.equal=function(a,b){return k("snap.util.equal",this,a,b).firstDefined()};k.on("snap.util.equal",function(e,k){var r,s;r=q(this.attr(e)||"");var x=this;if(r==+r&&k==+k)return{from:+r,to:+k,f:z};if("colour"==p[e])return r=a.color(r),s=a.color(k),{from:[r.r,r.g,r.b,r.opacity],to:[s.r,s.g,s.b,s.opacity],f:f};if("transform"==e||"gradientTransform"==e||"patternTransform"==e)return k instanceof a.Matrix&&(k=k.toTransformString()),a._.rgTransform.test(k)||(k=a._.svgTransform2string(k)),
w(r,k,function(){return x.getBBox(1)});if("d"==e||"path"==e)return r=a.path.toCubic(r,k),{from:u(r[0]),to:u(r[1]),f:n(r[0])};if("points"==e)return r=q(r).split(a._.separator),s=q(k).split(a._.separator),{from:r,to:s,f:function(a){return a}};aUnit=r.match(b);s=q(k).match(b);return aUnit&&aUnit==s?{from:parseFloat(r),to:parseFloat(k),f:d(aUnit)}:{from:this.asPX(e),to:this.asPX(e,k),f:z}})});C.plugin(function(a,v,y,C){var A=v.prototype,w="createTouch"in C.doc;v="click dblclick mousedown mousemove mouseout mouseover mouseup touchstart touchmove touchend touchcancel".split(" ");
var z={mousedown:"touchstart",mousemove:"touchmove",mouseup:"touchend"},d=function(a,b){var d="y"==a?"scrollTop":"scrollLeft",e=b&&b.node?b.node.ownerDocument:C.doc;return e[d in e.documentElement?"documentElement":"body"][d]},f=function(){this.returnValue=!1},n=function(){return this.originalEvent.preventDefault()},u=function(){this.cancelBubble=!0},p=function(){return this.originalEvent.stopPropagation()},b=function(){if(C.doc.addEventListener)return function(a,b,e,f){var k=w&&z[b]?z[b]:b,l=function(k){var l=
d("y",f),q=d("x",f);if(w&&z.hasOwnProperty(b))for(var r=0,u=k.targetTouches&&k.targetTouches.length;r<u;r++)if(k.targetTouches[r].target==a||a.contains(k.targetTouches[r].target)){u=k;k=k.targetTouches[r];k.originalEvent=u;k.preventDefault=n;k.stopPropagation=p;break}return e.call(f,k,k.clientX+q,k.clientY+l)};b!==k&&a.addEventListener(b,l,!1);a.addEventListener(k,l,!1);return function(){b!==k&&a.removeEventListener(b,l,!1);a.removeEventListener(k,l,!1);return!0}};if(C.doc.attachEvent)return function(a,
b,e,h){var k=function(a){a=a||h.node.ownerDocument.window.event;var b=d("y",h),k=d("x",h),k=a.clientX+k,b=a.clientY+b;a.preventDefault=a.preventDefault||f;a.stopPropagation=a.stopPropagation||u;return e.call(h,a,k,b)};a.attachEvent("on"+b,k);return function(){a.detachEvent("on"+b,k);return!0}}}(),q=[],e=function(a){for(var b=a.clientX,e=a.clientY,f=d("y"),l=d("x"),n,p=q.length;p--;){n=q[p];if(w)for(var r=a.touches&&a.touches.length,u;r--;){if(u=a.touches[r],u.identifier==n.el._drag.id||n.el.node.contains(u.target)){b=
u.clientX;e=u.clientY;(a.originalEvent?a.originalEvent:a).preventDefault();break}}else a.preventDefault();b+=l;e+=f;k("snap.drag.move."+n.el.id,n.move_scope||n.el,b-n.el._drag.x,e-n.el._drag.y,b,e,a)}},l=function(b){a.unmousemove(e).unmouseup(l);for(var d=q.length,f;d--;)f=q[d],f.el._drag={},k("snap.drag.end."+f.el.id,f.end_scope||f.start_scope||f.move_scope||f.el,b);q=[]};for(y=v.length;y--;)(function(d){a[d]=A[d]=function(e,f){a.is(e,"function")&&(this.events=this.events||[],this.events.push({name:d,
f:e,unbind:b(this.node||document,d,e,f||this)}));return this};a["un"+d]=A["un"+d]=function(a){for(var b=this.events||[],e=b.length;e--;)if(b[e].name==d&&(b[e].f==a||!a)){b[e].unbind();b.splice(e,1);!b.length&&delete this.events;break}return this}})(v[y]);A.hover=function(a,b,d,e){return this.mouseover(a,d).mouseout(b,e||d)};A.unhover=function(a,b){return this.unmouseover(a).unmouseout(b)};var r=[];A.drag=function(b,d,f,h,n,p){function u(r,v,w){(r.originalEvent||r).preventDefault();this._drag.x=v;
this._drag.y=w;this._drag.id=r.identifier;!q.length&&a.mousemove(e).mouseup(l);q.push({el:this,move_scope:h,start_scope:n,end_scope:p});d&&k.on("snap.drag.start."+this.id,d);b&&k.on("snap.drag.move."+this.id,b);f&&k.on("snap.drag.end."+this.id,f);k("snap.drag.start."+this.id,n||h||this,v,w,r)}if(!arguments.length){var v;return this.drag(function(a,b){this.attr({transform:v+(v?"T":"t")+[a,b]})},function(){v=this.transform().local})}this._drag={};r.push({el:this,start:u});this.mousedown(u);return this};
A.undrag=function(){for(var b=r.length;b--;)r[b].el==this&&(this.unmousedown(r[b].start),r.splice(b,1),k.unbind("snap.drag.*."+this.id));!r.length&&a.unmousemove(e).unmouseup(l);return this}});C.plugin(function(a,v,y,C){y=y.prototype;var A=/^\s*url\((.+)\)/,w=String,z=a._.$;a.filter={};y.filter=function(d){var f=this;"svg"!=f.type&&(f=f.paper);d=a.parse(w(d));var k=a._.id(),u=z("filter");z(u,{id:k,filterUnits:"userSpaceOnUse"});u.appendChild(d.node);f.defs.appendChild(u);return new v(u)};k.on("snap.util.getattr.filter",
function(){k.stop();var d=z(this.node,"filter");if(d)return(d=w(d).match(A))&&a.select(d[1])});k.on("snap.util.attr.filter",function(d){if(d instanceof v&&"filter"==d.type){k.stop();var f=d.node.id;f||(z(d.node,{id:d.id}),f=d.id);z(this.node,{filter:a.url(f)})}d&&"none"!=d||(k.stop(),this.node.removeAttribute("filter"))});a.filter.blur=function(d,f){null==d&&(d=2);return a.format('<feGaussianBlur stdDeviation="{def}"/>',{def:null==f?d:[d,f]})};a.filter.blur.toString=function(){return this()};a.filter.shadow=
function(d,f,k,u,p){"string"==typeof k&&(p=u=k,k=4);"string"!=typeof u&&(p=u,u="#000");null==k&&(k=4);null==p&&(p=1);null==d&&(d=0,f=2);null==f&&(f=d);u=a.color(u||"#000");return a.format('<feGaussianBlur in="SourceAlpha" stdDeviation="{blur}"/><feOffset dx="{dx}" dy="{dy}" result="offsetblur"/><feFlood flood-color="{color}"/><feComposite in2="offsetblur" operator="in"/><feComponentTransfer><feFuncA type="linear" slope="{opacity}"/></feComponentTransfer><feMerge><feMergeNode/><feMergeNode in="SourceGraphic"/></feMerge>',
{color:u,dx:d,dy:f,blur:k,opacity:p})};a.filter.shadow.toString=function(){return this()};a.filter.grayscale=function(d){null==d&&(d=1);return a.format('<feColorMatrix type="matrix" values="{a} {b} {c} 0 0 {d} {e} {f} 0 0 {g} {b} {h} 0 0 0 0 0 1 0"/>',{a:0.2126+0.7874*(1-d),b:0.7152-0.7152*(1-d),c:0.0722-0.0722*(1-d),d:0.2126-0.2126*(1-d),e:0.7152+0.2848*(1-d),f:0.0722-0.0722*(1-d),g:0.2126-0.2126*(1-d),h:0.0722+0.9278*(1-d)})};a.filter.grayscale.toString=function(){return this()};a.filter.sepia=
function(d){null==d&&(d=1);return a.format('<feColorMatrix type="matrix" values="{a} {b} {c} 0 0 {d} {e} {f} 0 0 {g} {h} {i} 0 0 0 0 0 1 0"/>',{a:0.393+0.607*(1-d),b:0.769-0.769*(1-d),c:0.189-0.189*(1-d),d:0.349-0.349*(1-d),e:0.686+0.314*(1-d),f:0.168-0.168*(1-d),g:0.272-0.272*(1-d),h:0.534-0.534*(1-d),i:0.131+0.869*(1-d)})};a.filter.sepia.toString=function(){return this()};a.filter.saturate=function(d){null==d&&(d=1);return a.format('<feColorMatrix type="saturate" values="{amount}"/>',{amount:1-
d})};a.filter.saturate.toString=function(){return this()};a.filter.hueRotate=function(d){return a.format('<feColorMatrix type="hueRotate" values="{angle}"/>',{angle:d||0})};a.filter.hueRotate.toString=function(){return this()};a.filter.invert=function(d){null==d&&(d=1);return a.format('<feComponentTransfer><feFuncR type="table" tableValues="{amount} {amount2}"/><feFuncG type="table" tableValues="{amount} {amount2}"/><feFuncB type="table" tableValues="{amount} {amount2}"/></feComponentTransfer>',{amount:d,
amount2:1-d})};a.filter.invert.toString=function(){return this()};a.filter.brightness=function(d){null==d&&(d=1);return a.format('<feComponentTransfer><feFuncR type="linear" slope="{amount}"/><feFuncG type="linear" slope="{amount}"/><feFuncB type="linear" slope="{amount}"/></feComponentTransfer>',{amount:d})};a.filter.brightness.toString=function(){return this()};a.filter.contrast=function(d){null==d&&(d=1);return a.format('<feComponentTransfer><feFuncR type="linear" slope="{amount}" intercept="{amount2}"/><feFuncG type="linear" slope="{amount}" intercept="{amount2}"/><feFuncB type="linear" slope="{amount}" intercept="{amount2}"/></feComponentTransfer>',
{amount:d,amount2:0.5-d/2})};a.filter.contrast.toString=function(){return this()}});return C});

]]> </script>
<script> <![CDATA[

(function (glob, factory) {
    // AMD support
    if (typeof define === "function" && define.amd) {
        // Define as an anonymous module
        define("Gadfly", ["Snap.svg"], function (Snap) {
            return factory(Snap);
        });
    } else {
        // Browser globals (glob is window)
        // Snap adds itself to window
        glob.Gadfly = factory(glob.Snap);
    }
}(this, function (Snap) {

var Gadfly = {};

// Get an x/y coordinate value in pixels
var xPX = function(fig, x) {
    var client_box = fig.node.getBoundingClientRect();
    return x * fig.node.viewBox.baseVal.width / client_box.width;
};

var yPX = function(fig, y) {
    var client_box = fig.node.getBoundingClientRect();
    return y * fig.node.viewBox.baseVal.height / client_box.height;
};


Snap.plugin(function (Snap, Element, Paper, global) {
    // Traverse upwards from a snap element to find and return the first
    // note with the "plotroot" class.
    Element.prototype.plotroot = function () {
        var element = this;
        while (!element.hasClass("plotroot") && element.parent() != null) {
            element = element.parent();
        }
        return element;
    };

    Element.prototype.svgroot = function () {
        var element = this;
        while (element.node.nodeName != "svg" && element.parent() != null) {
            element = element.parent();
        }
        return element;
    };

    Element.prototype.plotbounds = function () {
        var root = this.plotroot()
        var bbox = root.select(".guide.background").node.getBBox();
        return {
            x0: bbox.x,
            x1: bbox.x + bbox.width,
            y0: bbox.y,
            y1: bbox.y + bbox.height
        };
    };

    Element.prototype.plotcenter = function () {
        var root = this.plotroot()
        var bbox = root.select(".guide.background").node.getBBox();
        return {
            x: bbox.x + bbox.width / 2,
            y: bbox.y + bbox.height / 2
        };
    };

    // Emulate IE style mouseenter/mouseleave events, since Microsoft always
    // does everything right.
    // See: http://www.dynamic-tools.net/toolbox/isMouseLeaveOrEnter/
    var events = ["mouseenter", "mouseleave"];

    for (i in events) {
        (function (event_name) {
            var event_name = events[i];
            Element.prototype[event_name] = function (fn, scope) {
                if (Snap.is(fn, "function")) {
                    var fn2 = function (event) {
                        if (event.type != "mouseover" && event.type != "mouseout") {
                            return;
                        }

                        var reltg = event.relatedTarget ? event.relatedTarget :
                            event.type == "mouseout" ? event.toElement : event.fromElement;
                        while (reltg && reltg != this.node) reltg = reltg.parentNode;

                        if (reltg != this.node) {
                            return fn.apply(this, event);
                        }
                    };

                    if (event_name == "mouseenter") {
                        this.mouseover(fn2, scope);
                    } else {
                        this.mouseout(fn2, scope);
                    }
                }
                return this;
            };
        })(events[i]);
    }


    Element.prototype.mousewheel = function (fn, scope) {
        if (Snap.is(fn, "function")) {
            var el = this;
            var fn2 = function (event) {
                fn.apply(el, [event]);
            };
        }

        this.node.addEventListener(
            /Firefox/i.test(navigator.userAgent) ? "DOMMouseScroll" : "mousewheel",
            fn2);

        return this;
    };


    // Snap's attr function can be too slow for things like panning/zooming.
    // This is a function to directly update element attributes without going
    // through eve.
    Element.prototype.attribute = function(key, val) {
        if (val === undefined) {
            return this.node.getAttribute(key, val);
        } else {
            return this.node.setAttribute(key, val);
        }
    };
});


// When the plot is moused over, emphasize the grid lines.
Gadfly.plot_mouseover = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);

    var xgridlines = root.select(".xgridlines"),
        ygridlines = root.select(".ygridlines");

    xgridlines.data("unfocused_strokedash",
                    xgridlines.attr("stroke-dasharray").replace(/px/g, "mm"))
    ygridlines.data("unfocused_strokedash",
                    ygridlines.attr("stroke-dasharray").replace(/px/g, "mm"))

    // emphasize grid lines
    var destcolor = root.data("focused_xgrid_color");
    xgridlines.attr("stroke-dasharray", "none")
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    destcolor = root.data("focused_ygrid_color");
    ygridlines.attr("stroke-dasharray", "none")
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    // reveal zoom slider
    root.select(".zoomslider")
        .animate({opacity: 1.0}, 250);
};


// Unemphasize grid lines on mouse out.
Gadfly.plot_mouseout = function(event) {
    var root = this.plotroot();
    var xgridlines = root.select(".xgridlines"),
        ygridlines = root.select(".ygridlines");

    var destcolor = root.data("unfocused_xgrid_color");

    xgridlines.attr("stroke-dasharray", xgridlines.data("unfocused_strokedash"))
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    destcolor = root.data("unfocused_ygrid_color");
    ygridlines.attr("stroke-dasharray", ygridlines.data("unfocused_strokedash"))
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    // hide zoom slider
    root.select(".zoomslider")
        .animate({opacity: 0.0}, 250);
};


var set_geometry_transform = function(root, tx, ty, scale) {
    var xscalable = root.hasClass("xscalable"),
        yscalable = root.hasClass("yscalable");

    var old_scale = root.data("scale");

    var xscale = xscalable ? scale : 1.0,
        yscale = yscalable ? scale : 1.0;

    tx = xscalable ? tx : 0.0;
    ty = yscalable ? ty : 0.0;

    var t = new Snap.Matrix().translate(tx, ty).scale(xscale, yscale);

    root.selectAll(".geometry, image")
        .forEach(function (element, i) {
            element.transform(t);
        });

    bounds = root.plotbounds();

    if (yscalable) {
        var xfixed_t = new Snap.Matrix().translate(0, ty).scale(1.0, yscale);
        root.selectAll(".xfixed")
            .forEach(function (element, i) {
                element.transform(xfixed_t);
            });

        root.select(".ylabels")
            .transform(xfixed_t)
            .selectAll("text")
            .forEach(function (element, i) {
                if (element.attribute("gadfly:inscale") == "true") {
                    var cx = element.asPX("x"),
                        cy = element.asPX("y");
                    var st = element.data("static_transform");
                    unscale_t = new Snap.Matrix();
                    unscale_t.scale(1, 1/scale, cx, cy).add(st);
                    element.transform(unscale_t);

                    var y = cy * scale + ty;
                    element.attr("visibility",
                        bounds.y0 <= y && y <= bounds.y1 ? "visible" : "hidden");
                }
            });
    }

    if (xscalable) {
        var yfixed_t = new Snap.Matrix().translate(tx, 0).scale(xscale, 1.0);
        var xtrans = new Snap.Matrix().translate(tx, 0);
        root.selectAll(".yfixed")
            .forEach(function (element, i) {
                element.transform(yfixed_t);
            });

        root.select(".xlabels")
            .transform(yfixed_t)
            .selectAll("text")
            .forEach(function (element, i) {
                if (element.attribute("gadfly:inscale") == "true") {
                    var cx = element.asPX("x"),
                        cy = element.asPX("y");
                    var st = element.data("static_transform");
                    unscale_t = new Snap.Matrix();
                    unscale_t.scale(1/scale, 1, cx, cy).add(st);

                    element.transform(unscale_t);

                    var x = cx * scale + tx;
                    element.attr("visibility",
                        bounds.x0 <= x && x <= bounds.x1 ? "visible" : "hidden");
                    }
            });
    }

    // we must unscale anything that is scale invariance: widths, raiduses, etc.
    var size_attribs = ["font-size"];
    var unscaled_selection = ".geometry, .geometry *";
    if (xscalable) {
        size_attribs.push("rx");
        unscaled_selection += ", .xgridlines";
    }
    if (yscalable) {
        size_attribs.push("ry");
        unscaled_selection += ", .ygridlines";
    }

    root.selectAll(unscaled_selection)
        .forEach(function (element, i) {
            // circle need special help
            if (element.node.nodeName == "circle") {
                var cx = element.attribute("cx"),
                    cy = element.attribute("cy");
                unscale_t = new Snap.Matrix().scale(1/xscale, 1/yscale,
                                                        cx, cy);
                element.transform(unscale_t);
                return;
            }

            for (i in size_attribs) {
                var key = size_attribs[i];
                var val = parseFloat(element.attribute(key));
                if (val !== undefined && val != 0 && !isNaN(val)) {
                    element.attribute(key, val * old_scale / scale);
                }
            }
        });
};


// Find the most appropriate tick scale and update label visibility.
var update_tickscale = function(root, scale, axis) {
    if (!root.hasClass(axis + "scalable")) return;

    var tickscales = root.data(axis + "tickscales");
    var best_tickscale = 1.0;
    var best_tickscale_dist = Infinity;
    for (tickscale in tickscales) {
        var dist = Math.abs(Math.log(tickscale) - Math.log(scale));
        if (dist < best_tickscale_dist) {
            best_tickscale_dist = dist;
            best_tickscale = tickscale;
        }
    }

    if (best_tickscale != root.data(axis + "tickscale")) {
        root.data(axis + "tickscale", best_tickscale);
        var mark_inscale_gridlines = function (element, i) {
            var inscale = element.attr("gadfly:scale") == best_tickscale;
            element.attribute("gadfly:inscale", inscale);
            element.attr("visibility", inscale ? "visible" : "hidden");
        };

        var mark_inscale_labels = function (element, i) {
            var inscale = element.attr("gadfly:scale") == best_tickscale;
            element.attribute("gadfly:inscale", inscale);
            element.attr("visibility", inscale ? "visible" : "hidden");
        };

        root.select("." + axis + "gridlines").selectAll("path").forEach(mark_inscale_gridlines);
        root.select("." + axis + "labels").selectAll("text").forEach(mark_inscale_labels);
    }
};


var set_plot_pan_zoom = function(root, tx, ty, scale) {
    var old_scale = root.data("scale");
    var bounds = root.plotbounds();

    var width = bounds.x1 - bounds.x0,
        height = bounds.y1 - bounds.y0;

    // compute the viewport derived from tx, ty, and scale
    var x_min = -width * scale - (scale * width - width),
        x_max = width * scale,
        y_min = -height * scale - (scale * height - height),
        y_max = height * scale;

    var x0 = bounds.x0 - scale * bounds.x0,
        y0 = bounds.y0 - scale * bounds.y0;

    var tx = Math.max(Math.min(tx - x0, x_max), x_min),
        ty = Math.max(Math.min(ty - y0, y_max), y_min);

    tx += x0;
    ty += y0;

    // when the scale change, we may need to alter which set of
    // ticks is being displayed
    if (scale != old_scale) {
        update_tickscale(root, scale, "x");
        update_tickscale(root, scale, "y");
    }

    set_geometry_transform(root, tx, ty, scale);

    root.data("scale", scale);
    root.data("tx", tx);
    root.data("ty", ty);
};


var scale_centered_translation = function(root, scale) {
    var bounds = root.plotbounds();

    var width = bounds.x1 - bounds.x0,
        height = bounds.y1 - bounds.y0;

    var tx0 = root.data("tx"),
        ty0 = root.data("ty");

    var scale0 = root.data("scale");

    // how off from center the current view is
    var xoff = tx0 - (bounds.x0 * (1 - scale0) + (width * (1 - scale0)) / 2),
        yoff = ty0 - (bounds.y0 * (1 - scale0) + (height * (1 - scale0)) / 2);

    // rescale offsets
    xoff = xoff * scale / scale0;
    yoff = yoff * scale / scale0;

    // adjust for the panel position being scaled
    var x_edge_adjust = bounds.x0 * (1 - scale),
        y_edge_adjust = bounds.y0 * (1 - scale);

    return {
        x: xoff + x_edge_adjust + (width - width * scale) / 2,
        y: yoff + y_edge_adjust + (height - height * scale) / 2
    };
};


// Initialize data for panning zooming if it isn't already.
var init_pan_zoom = function(root) {
    if (root.data("zoompan-ready")) {
        return;
    }

    // The non-scaling-stroke trick. Rather than try to correct for the
    // stroke-width when zooming, we force it to a fixed value.
    var px_per_mm = root.node.getCTM().a;

    // Drag events report deltas in pixels, which we'd like to convert to
    // millimeters.
    root.data("px_per_mm", px_per_mm);

    root.selectAll("path")
        .forEach(function (element, i) {
        sw = element.asPX("stroke-width") * px_per_mm;
        if (sw > 0) {
            element.attribute("stroke-width", sw);
            element.attribute("vector-effect", "non-scaling-stroke");
        }
    });

    // Store ticks labels original tranformation
    root.selectAll(".xlabels > text, .ylabels > text")
        .forEach(function (element, i) {
            var lm = element.transform().localMatrix;
            element.data("static_transform",
                new Snap.Matrix(lm.a, lm.b, lm.c, lm.d, lm.e, lm.f));
        });

    if (root.data("tx") === undefined) root.data("tx", 0);
    if (root.data("ty") === undefined) root.data("ty", 0);
    if (root.data("scale") === undefined) root.data("scale", 1.0);
    if (root.data("xtickscales") === undefined) {

        // index all the tick scales that are listed
        var xtickscales = {};
        var ytickscales = {};
        var add_x_tick_scales = function (element, i) {
            xtickscales[element.attribute("gadfly:scale")] = true;
        };
        var add_y_tick_scales = function (element, i) {
            ytickscales[element.attribute("gadfly:scale")] = true;
        };

        root.select(".xgridlines").selectAll("path").forEach(add_x_tick_scales);
        root.select(".ygridlines").selectAll("path").forEach(add_y_tick_scales);
        root.select(".xlabels").selectAll("text").forEach(add_x_tick_scales);
        root.select(".ylabels").selectAll("text").forEach(add_y_tick_scales);

        root.data("xtickscales", xtickscales);
        root.data("ytickscales", ytickscales);
        root.data("xtickscale", 1.0);
    }

    var min_scale = 1.0, max_scale = 1.0;
    for (scale in xtickscales) {
        min_scale = Math.min(min_scale, scale);
        max_scale = Math.max(max_scale, scale);
    }
    for (scale in ytickscales) {
        min_scale = Math.min(min_scale, scale);
        max_scale = Math.max(max_scale, scale);
    }
    root.data("min_scale", min_scale);
    root.data("max_scale", max_scale);

    // store the original positions of labels
    root.select(".xlabels")
        .selectAll("text")
        .forEach(function (element, i) {
            element.data("x", element.asPX("x"));
        });

    root.select(".ylabels")
        .selectAll("text")
        .forEach(function (element, i) {
            element.data("y", element.asPX("y"));
        });

    // mark grid lines and ticks as in or out of scale.
    var mark_inscale = function (element, i) {
        element.attribute("gadfly:inscale", element.attribute("gadfly:scale") == 1.0);
    };

    root.select(".xgridlines").selectAll("path").forEach(mark_inscale);
    root.select(".ygridlines").selectAll("path").forEach(mark_inscale);
    root.select(".xlabels").selectAll("text").forEach(mark_inscale);
    root.select(".ylabels").selectAll("text").forEach(mark_inscale);

    // figure out the upper ond lower bounds on panning using the maximum
    // and minum grid lines
    var bounds = root.plotbounds();
    var pan_bounds = {
        x0: 0.0,
        y0: 0.0,
        x1: 0.0,
        y1: 0.0
    };

    root.select(".xgridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                var bbox = element.node.getBBox();
                if (bounds.x1 - bbox.x < pan_bounds.x0) {
                    pan_bounds.x0 = bounds.x1 - bbox.x;
                }
                if (bounds.x0 - bbox.x > pan_bounds.x1) {
                    pan_bounds.x1 = bounds.x0 - bbox.x;
                }
            }
        });

    root.select(".ygridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                var bbox = element.node.getBBox();
                if (bounds.y1 - bbox.y < pan_bounds.y0) {
                    pan_bounds.y0 = bounds.y1 - bbox.y;
                }
                if (bounds.y0 - bbox.y > pan_bounds.y1) {
                    pan_bounds.y1 = bounds.y0 - bbox.y;
                }
            }
        });

    // nudge these values a little
    pan_bounds.x0 -= 5;
    pan_bounds.x1 += 5;
    pan_bounds.y0 -= 5;
    pan_bounds.y1 += 5;
    root.data("pan_bounds", pan_bounds);

    // Set all grid lines at scale 1.0 to visible. Out of bounds lines
    // will be clipped.
    root.select(".xgridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                element.attr("visibility", "visible");
            }
        });

    root.select(".ygridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                element.attr("visibility", "visible");
            }
        });

    root.data("zoompan-ready", true)
};


// Panning
Gadfly.guide_background_drag_onmove = function(dx, dy, x, y, event) {
    var root = this.plotroot();
    var px_per_mm = root.data("px_per_mm");
    dx /= px_per_mm;
    dy /= px_per_mm;

    var tx0 = root.data("tx"),
        ty0 = root.data("ty");

    var dx0 = root.data("dx"),
        dy0 = root.data("dy");

    root.data("dx", dx);
    root.data("dy", dy);

    dx = dx - dx0;
    dy = dy - dy0;

    var tx = tx0 + dx,
        ty = ty0 + dy;

    set_plot_pan_zoom(root, tx, ty, root.data("scale"));
};


Gadfly.guide_background_drag_onstart = function(x, y, event) {
    var root = this.plotroot();
    root.data("dx", 0);
    root.data("dy", 0);
    init_pan_zoom(root);
};


Gadfly.guide_background_drag_onend = function(event) {
    var root = this.plotroot();
};


Gadfly.guide_background_scroll = function(event) {
    if (event.shiftKey) {
        var root = this.plotroot();
        init_pan_zoom(root);
        var new_scale = root.data("scale") * Math.pow(2, 0.002 * event.wheelDelta);
        new_scale = Math.max(
            root.data("min_scale"),
            Math.min(root.data("max_scale"), new_scale))
        update_plot_scale(root, new_scale);
        event.stopPropagation();
    }
};


Gadfly.zoomslider_button_mouseover = function(event) {
    this.select(".button_logo")
         .animate({fill: this.data("mouseover_color")}, 100);
};


Gadfly.zoomslider_button_mouseout = function(event) {
     this.select(".button_logo")
         .animate({fill: this.data("mouseout_color")}, 100);
};


Gadfly.zoomslider_zoomout_click = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);
    var min_scale = root.data("min_scale"),
        scale = root.data("scale");
    Snap.animate(
        scale,
        Math.max(min_scale, scale / 1.5),
        function (new_scale) {
            update_plot_scale(root, new_scale);
        },
        200);
};


Gadfly.zoomslider_zoomin_click = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);
    var max_scale = root.data("max_scale"),
        scale = root.data("scale");

    Snap.animate(
        scale,
        Math.min(max_scale, scale * 1.5),
        function (new_scale) {
            update_plot_scale(root, new_scale);
        },
        200);
};


Gadfly.zoomslider_track_click = function(event) {
    // TODO
};


Gadfly.zoomslider_thumb_mousedown = function(event) {
    this.animate({fill: this.data("mouseover_color")}, 100);
};


Gadfly.zoomslider_thumb_mouseup = function(event) {
    this.animate({fill: this.data("mouseout_color")}, 100);
};


// compute the position in [0, 1] of the zoom slider thumb from the current scale
var slider_position_from_scale = function(scale, min_scale, max_scale) {
    if (scale >= 1.0) {
        return 0.5 + 0.5 * (Math.log(scale) / Math.log(max_scale));
    }
    else {
        return 0.5 * (Math.log(scale) - Math.log(min_scale)) / (0 - Math.log(min_scale));
    }
}


var update_plot_scale = function(root, new_scale) {
    var trans = scale_centered_translation(root, new_scale);
    set_plot_pan_zoom(root, trans.x, trans.y, new_scale);

    root.selectAll(".zoomslider_thumb")
        .forEach(function (element, i) {
            var min_pos = element.data("min_pos"),
                max_pos = element.data("max_pos"),
                min_scale = root.data("min_scale"),
                max_scale = root.data("max_scale");
            var xmid = (min_pos + max_pos) / 2;
            var xpos = slider_position_from_scale(new_scale, min_scale, max_scale);
            element.transform(new Snap.Matrix().translate(
                Math.max(min_pos, Math.min(
                         max_pos, min_pos + (max_pos - min_pos) * xpos)) - xmid, 0));
    });
};


Gadfly.zoomslider_thumb_dragmove = function(dx, dy, x, y) {
    var root = this.plotroot();
    var min_pos = this.data("min_pos"),
        max_pos = this.data("max_pos"),
        min_scale = root.data("min_scale"),
        max_scale = root.data("max_scale"),
        old_scale = root.data("old_scale");

    var px_per_mm = root.data("px_per_mm");
    dx /= px_per_mm;
    dy /= px_per_mm;

    var xmid = (min_pos + max_pos) / 2;
    var xpos = slider_position_from_scale(old_scale, min_scale, max_scale) +
                   dx / (max_pos - min_pos);

    // compute the new scale
    var new_scale;
    if (xpos >= 0.5) {
        new_scale = Math.exp(2.0 * (xpos - 0.5) * Math.log(max_scale));
    }
    else {
        new_scale = Math.exp(2.0 * xpos * (0 - Math.log(min_scale)) +
                        Math.log(min_scale));
    }
    new_scale = Math.min(max_scale, Math.max(min_scale, new_scale));

    update_plot_scale(root, new_scale);
};


Gadfly.zoomslider_thumb_dragstart = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);

    // keep track of what the scale was when we started dragging
    root.data("old_scale", root.data("scale"));
};


Gadfly.zoomslider_thumb_dragend = function(event) {
};


var toggle_color_class = function(root, color_class, ison) {
    var guides = root.selectAll(".guide." + color_class + ",.guide ." + color_class);
    var geoms = root.selectAll(".geometry." + color_class + ",.geometry ." + color_class);
    if (ison) {
        guides.animate({opacity: 0.5}, 250);
        geoms.animate({opacity: 0.0}, 250);
    } else {
        guides.animate({opacity: 1.0}, 250);
        geoms.animate({opacity: 1.0}, 250);
    }
};


Gadfly.colorkey_swatch_click = function(event) {
    var root = this.plotroot();
    var color_class = this.data("color_class");

    if (event.shiftKey) {
        root.selectAll(".colorkey text")
            .forEach(function (element) {
                var other_color_class = element.data("color_class");
                if (other_color_class != color_class) {
                    toggle_color_class(root, other_color_class,
                                       element.attr("opacity") == 1.0);
                }
            });
    } else {
        toggle_color_class(root, color_class, this.attr("opacity") == 1.0);
    }
};


return Gadfly;

}));


//@ sourceURL=gadfly.js

(function (glob, factory) {
    // AMD support
      if (typeof require === "function" && typeof define === "function" && define.amd) {
        require(["Snap.svg", "Gadfly"], function (Snap, Gadfly) {
            factory(Snap, Gadfly);
        });
      } else {
          factory(glob.Snap, glob.Gadfly);
      }
})(window, function (Snap, Gadfly) {
    var fig = Snap("#fig-371e21ceeb8a4893938846e9321c8d7c");
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-4")
   .drag(function() {}, function() {}, function() {});
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-6")
   .data("color_class", "color_f1")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-7")
   .data("color_class", "color_f2")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-9")
   .data("color_class", "color_f1")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-10")
   .data("color_class", "color_f2")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-13")
   .mouseenter(Gadfly.plot_mouseover)
.mouseleave(Gadfly.plot_mouseout)
.mousewheel(Gadfly.guide_background_scroll)
.drag(Gadfly.guide_background_drag_onmove,
      Gadfly.guide_background_drag_onstart,
      Gadfly.guide_background_drag_onend)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-17")
   .plotroot().data("unfocused_ygrid_color", "#D0D0E0")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-17")
   .plotroot().data("focused_ygrid_color", "#A0A0A0")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-147")
   .plotroot().data("unfocused_xgrid_color", "#D0D0E0")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-147")
   .plotroot().data("focused_xgrid_color", "#A0A0A0")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-264")
   .data("mouseover_color", "#cd5c5c")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-264")
   .data("mouseout_color", "#6a6a6a")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-264")
   .click(Gadfly.zoomslider_zoomin_click)
.mouseenter(Gadfly.zoomslider_button_mouseover)
.mouseleave(Gadfly.zoomslider_button_mouseout)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-268")
   .data("max_pos", 97.77)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-268")
   .data("min_pos", 80.77)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-268")
   .click(Gadfly.zoomslider_track_click);
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-270")
   .data("max_pos", 97.77)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-270")
   .data("min_pos", 80.77)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-270")
   .data("mouseover_color", "#cd5c5c")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-270")
   .data("mouseout_color", "#6a6a6a")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-270")
   .drag(Gadfly.zoomslider_thumb_dragmove,
     Gadfly.zoomslider_thumb_dragstart,
     Gadfly.zoomslider_thumb_dragend)
.mousedown(Gadfly.zoomslider_thumb_mousedown)
.mouseup(Gadfly.zoomslider_thumb_mouseup)
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-272")
   .data("mouseover_color", "#cd5c5c")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-272")
   .data("mouseout_color", "#6a6a6a")
;
fig.select("#fig-371e21ceeb8a4893938846e9321c8d7c-element-272")
   .click(Gadfly.zoomslider_zoomout_click)
.mouseenter(Gadfly.zoomslider_button_mouseover)
.mouseleave(Gadfly.zoomslider_button_mouseout)
;
    });
]]> </script>
</svg>




The inverse of (9) is

$$
x={\frac{1}{2}}N[1-(1-2r_{x})^{1/N}]
\tag{10}
$$

In the second approach for deriving map functions, recombination is
modeled in two adjacent intervals. Suppose three loci $A$, $B$, and $C$
are ordered as $ABC$ with a map distance of $x$ between $A$ and $B$, and
a distance of $h$ between $B$ and $C$. Let $M(x)$ be the map function
that we wish to derive that transforms map distances to recombination
rates. It is assumed that when $x$ is sufficiently small,
$r_{x}=M(x)=x$.

Also, let $g_{\epsilon_i}$ denote the
probability of the recombination event indexed by $\epsilon_i$; for example,
$g_{10}$ is the probability of a recombination in the first interval and
no recombination in the second interval.

Using this notation, the probability $r_{AC}$ of a recombination between
$A$ and $C$ can be written as

$$r_{AC}=g_{10}+g_{01}$$

If there is no interference,

$$\begin{split}
r_{AC}
& =g_{10}+g_{01}\\
& =r_{AB}(1-r_{BC})+(1-r_{AB})r_{BC}\\
& =r_{AB}+r_{BC}-2r_{AB}r_{BC}
\end{split}
\tag{11}
$$

Recall that $r_{AB}r_{BC}=g_{11}$ is the probability of a double
recombination when interference is absent. When interference is present,
the probability of a double recombination is given by ([g11]). Thus,
when interference is present, the probability of a recombination between
$A$ and $C$ can be written as

$$
r_{AC}=r_{AB}+r_{BC}-2cr_{AB}r_{BC}
\tag{12}
$$

where $c$ is the coefficient of coincidence. Now, ([rac-interference])
is rewritten using the map function $M(.)$ in place of the recombination
rates:

$$
M(x+h)=M(x)+M(h)-2cM(x)M(h)
\tag{13}
$$

The above equation can be rearranged as

$$
\frac{M(x+h)-M(x)}{h}=\frac{M(h)-2cM(x)M(h)}{h}
\tag{14}
$$

As $h\to0$, $\frac{M(h)}{h}\to1$. Thus, taking the limit as $h\to0$, on
both sides of ([rac-derivative-eq]) gives

$$
\frac{dr_{x}}{dx}=1-2cr_{x}
\tag{15}
$$

Letting $c=1$ and solving (15) gives Haldane’s map function
(6). When $c=1$, recombination in the two intervals are
independent; this assumption is implicit in the Poisson distribution.

Letting $c=2r_{x}$ gives the **Kosambi map function**

>$$
r_{x}={\frac{1}{2}}\frac{e^{4x}-1}{e^{4x}+1}
\tag{16}
$$

with inverse

$$
x=\frac{1}{4}\ln\frac{1+2r_{x}}{1-2r_{x}}
\tag{17}
$$

Several other map functions derived from (15) by assuming
different assumptions about $c$ are given in AHGL (pp 14–17). Map
functions derived from (15) with $c\neq1$ are not suitable
for linkage analysis with more than three loci (AHGL pp 124–127).


    @manipulate for N=2:10
        plot([x -> x<N/2 ? 0.5(1 - (1 - 2x/N)^N):0.5, x -> 0.5(1 - exp(-2x)), x -> 0.5((exp(4x)-1)/(exp(4x)+1))] , 0,2.0, 
        Guide.title("Karlin's (f<sub>1</sub>), Haldane's (f<sub>2</sub>) and Kosambi's (f<sub>3</sub>)  Map Functions"),
            Guide.ylabel("Recombination Rate"), Guide.xlabel("Map Distance"),
            Guide.colorkey("Map Function")
        )
    end








<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg"
     xmlns:xlink="http://www.w3.org/1999/xlink"
     xmlns:gadfly="http://www.gadflyjl.org/ns"
     version="1.2"
     width="141.42mm" height="100mm" viewBox="0 0 141.42 100"
     stroke="none"
     fill="#000000"
     stroke-width="0.3"
     font-size="3.88"

     id="fig-8226a61cd72e412e8cc8f049f5a87d42">
<g class="plotroot xscalable yscalable" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-1">
  <g font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" fill="#564A55" stroke="none" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-2">
    <text x="66.2" y="92" text-anchor="middle">Map Distance</text>
  </g>
  <g class="guide xlabels" font-size="2.82" font-family="'PT Sans Caption','Helvetica Neue','Helvetica',sans-serif" fill="#6C606B" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-3">
    <text x="-93.29" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-2.5</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-2.0</text>
    <text x="-47.72" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-1.5</text>
    <text x="-24.94" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-1.0</text>
    <text x="-2.15" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">-0.5</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">0.0</text>
    <text x="43.42" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">0.5</text>
    <text x="66.2" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">1.0</text>
    <text x="88.99" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">1.5</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="visible">2.0</text>
    <text x="134.56" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">2.5</text>
    <text x="157.34" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">3.0</text>
    <text x="180.12" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">3.5</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">4.0</text>
    <text x="225.69" y="84.39" text-anchor="middle" gadfly:scale="1.0" visibility="hidden">4.5</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-2.0</text>
    <text x="-65.95" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.9</text>
    <text x="-61.39" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.8</text>
    <text x="-56.84" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.7</text>
    <text x="-52.28" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.6</text>
    <text x="-47.72" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.5</text>
    <text x="-43.17" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.4</text>
    <text x="-38.61" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.3</text>
    <text x="-34.05" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.2</text>
    <text x="-29.49" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.1</text>
    <text x="-24.94" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-1.0</text>
    <text x="-20.38" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.9</text>
    <text x="-15.82" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.8</text>
    <text x="-11.27" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.7</text>
    <text x="-6.71" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.6</text>
    <text x="-2.15" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.5</text>
    <text x="2.4" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.4</text>
    <text x="6.96" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.3</text>
    <text x="11.52" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.2</text>
    <text x="16.07" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">-0.1</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.0</text>
    <text x="25.19" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.1</text>
    <text x="29.75" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.2</text>
    <text x="34.3" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.3</text>
    <text x="38.86" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.4</text>
    <text x="43.42" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.5</text>
    <text x="47.97" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.6</text>
    <text x="52.53" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.7</text>
    <text x="57.09" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.8</text>
    <text x="61.64" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">0.9</text>
    <text x="66.2" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.0</text>
    <text x="70.76" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.1</text>
    <text x="75.31" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.2</text>
    <text x="79.87" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.3</text>
    <text x="84.43" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.4</text>
    <text x="88.99" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.5</text>
    <text x="93.54" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.6</text>
    <text x="98.1" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.7</text>
    <text x="102.66" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.8</text>
    <text x="107.21" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">1.9</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.0</text>
    <text x="116.33" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.1</text>
    <text x="120.88" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.2</text>
    <text x="125.44" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.3</text>
    <text x="130" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.4</text>
    <text x="134.56" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.5</text>
    <text x="139.11" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.6</text>
    <text x="143.67" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.7</text>
    <text x="148.23" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.8</text>
    <text x="152.78" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">2.9</text>
    <text x="157.34" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.0</text>
    <text x="161.9" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.1</text>
    <text x="166.45" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.2</text>
    <text x="171.01" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.3</text>
    <text x="175.57" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.4</text>
    <text x="180.12" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.5</text>
    <text x="184.68" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.6</text>
    <text x="189.24" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.7</text>
    <text x="193.8" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.8</text>
    <text x="198.35" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">3.9</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="10.0" visibility="hidden">4.0</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">-2</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">0</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">2</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="0.5" visibility="hidden">4</text>
    <text x="-70.51" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-2.0</text>
    <text x="-61.39" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.8</text>
    <text x="-52.28" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.6</text>
    <text x="-43.17" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.4</text>
    <text x="-34.05" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.2</text>
    <text x="-24.94" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-1.0</text>
    <text x="-15.82" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.8</text>
    <text x="-6.71" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.6</text>
    <text x="2.4" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.4</text>
    <text x="11.52" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">-0.2</text>
    <text x="20.63" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.0</text>
    <text x="29.75" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.2</text>
    <text x="38.86" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.4</text>
    <text x="47.97" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.6</text>
    <text x="57.09" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">0.8</text>
    <text x="66.2" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.0</text>
    <text x="75.31" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.2</text>
    <text x="84.43" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.4</text>
    <text x="93.54" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.6</text>
    <text x="102.66" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">1.8</text>
    <text x="111.77" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.0</text>
    <text x="120.88" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.2</text>
    <text x="130" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.4</text>
    <text x="139.11" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.6</text>
    <text x="148.23" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">2.8</text>
    <text x="157.34" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.0</text>
    <text x="166.45" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.2</text>
    <text x="175.57" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.4</text>
    <text x="184.68" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.6</text>
    <text x="193.8" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">3.8</text>
    <text x="202.91" y="84.39" text-anchor="middle" gadfly:scale="5.0" visibility="hidden">4.0</text>
  </g>
  <g class="guide colorkey" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-4">
    <g fill="#4C404B" font-size="2.82" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-5">
      <text x="118.24" y="45.1" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-6" class="color_f1">f<tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">1</tspan><tspan dy="-0.498000em"></tspan></text>
      <text x="118.24" y="50.04" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-7" class="color_f2">f<tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">2</tspan><tspan dy="-0.498000em"></tspan></text>
      <text x="118.24" y="54.98" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-8" class="color_f3">f<tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">3</tspan><tspan dy="-0.498000em"></tspan></text>
    </g>
    <g stroke="none" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-9">
      <rect x="114.77" y="43.86" width="2.47" height="2.47" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-10" fill="#00BFFF" class="color_f1"/>
      <rect x="114.77" y="48.8" width="2.47" height="2.47" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-11" fill="#D4CA3A" class="color_f2"/>
      <rect x="114.77" y="53.74" width="2.47" height="2.47" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-12" fill="#FF5EA0" class="color_f3"/>
    </g>
    <g fill="#362A35" font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" stroke="none" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-13">
      <text x="114.77" y="39.96" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-14">Map Function</text>
    </g>
  </g>
  <g clip-path="url(#fig-8226a61cd72e412e8cc8f049f5a87d42-element-16)" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-15">
    <g pointer-events="visible" opacity="1" fill="none" stroke="none" class="guide background" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-17">
      <rect x="18.63" y="14.42" width="95.14" height="66.3" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-18"/>
    </g>
    <g class="guide ygridlines xfixed" stroke-dasharray="0.5,0.5" stroke-width="0.2" stroke="#D0D0E0" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-19">
      <path fill="none" d="M18.63,153.47 L 113.77 153.47" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-20" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-21" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,128.55 L 113.77 128.55" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-22" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,116.09 L 113.77 116.09" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-23" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,103.63 L 113.77 103.63" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-24" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,91.17 L 113.77 91.17" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-25" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-26" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,66.26 L 113.77 66.26" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-27" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,53.8 L 113.77 53.8" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-28" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,41.34 L 113.77 41.34" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-29" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,28.88 L 113.77 28.88" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-30" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-31" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M18.63,3.96 L 113.77 3.96" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-32" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-8.5 L 113.77 -8.5" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-33" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-20.96 L 113.77 -20.96" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-34" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-33.42 L 113.77 -33.42" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-35" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-36" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-58.34 L 113.77 -58.34" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-37" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-38" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,138.52 L 113.77 138.52" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-39" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,136.03 L 113.77 136.03" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-40" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,133.54 L 113.77 133.54" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-41" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,131.04 L 113.77 131.04" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-42" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,128.55 L 113.77 128.55" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-43" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,126.06 L 113.77 126.06" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-44" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,123.57 L 113.77 123.57" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-45" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,121.08 L 113.77 121.08" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-46" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,118.59 L 113.77 118.59" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-47" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,116.09 L 113.77 116.09" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-48" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,113.6 L 113.77 113.6" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-49" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,111.11 L 113.77 111.11" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-50" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,108.62 L 113.77 108.62" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-51" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,106.13 L 113.77 106.13" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-52" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,103.63 L 113.77 103.63" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-53" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,101.14 L 113.77 101.14" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-54" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,98.65 L 113.77 98.65" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-55" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,96.16 L 113.77 96.16" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-56" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,93.67 L 113.77 93.67" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-57" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,91.17 L 113.77 91.17" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-58" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,88.68 L 113.77 88.68" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-59" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,86.19 L 113.77 86.19" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-60" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,83.7 L 113.77 83.7" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-61" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,81.21 L 113.77 81.21" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-62" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-63" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,76.22 L 113.77 76.22" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-64" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,73.73 L 113.77 73.73" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-65" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,71.24 L 113.77 71.24" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-66" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,68.75 L 113.77 68.75" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-67" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,66.26 L 113.77 66.26" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-68" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,63.76 L 113.77 63.76" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-69" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,61.27 L 113.77 61.27" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-70" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,58.78 L 113.77 58.78" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-71" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,56.29 L 113.77 56.29" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-72" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,53.8 L 113.77 53.8" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-73" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,51.3 L 113.77 51.3" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-74" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,48.81 L 113.77 48.81" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-75" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,46.32 L 113.77 46.32" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-76" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,43.83 L 113.77 43.83" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-77" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,41.34 L 113.77 41.34" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-78" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,38.84 L 113.77 38.84" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-79" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,36.35 L 113.77 36.35" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-80" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,33.86 L 113.77 33.86" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-81" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,31.37 L 113.77 31.37" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-82" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,28.88 L 113.77 28.88" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-83" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,26.39 L 113.77 26.39" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-84" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,23.89 L 113.77 23.89" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-85" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,21.4 L 113.77 21.4" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-86" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,18.91 L 113.77 18.91" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-87" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-88" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,13.93 L 113.77 13.93" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-89" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,11.43 L 113.77 11.43" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-90" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,8.94 L 113.77 8.94" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-91" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,6.45 L 113.77 6.45" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-92" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,3.96 L 113.77 3.96" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-93" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,1.47 L 113.77 1.47" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-94" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-1.03 L 113.77 -1.03" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-95" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-3.52 L 113.77 -3.52" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-96" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-6.01 L 113.77 -6.01" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-97" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-8.5 L 113.77 -8.5" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-98" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-10.99 L 113.77 -10.99" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-99" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-13.49 L 113.77 -13.49" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-100" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-15.98 L 113.77 -15.98" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-101" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-18.47 L 113.77 -18.47" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-102" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-20.96 L 113.77 -20.96" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-103" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-23.45 L 113.77 -23.45" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-104" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-25.94 L 113.77 -25.94" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-105" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-28.44 L 113.77 -28.44" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-106" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-30.93 L 113.77 -30.93" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-107" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-33.42 L 113.77 -33.42" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-108" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-35.91 L 113.77 -35.91" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-109" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-38.4 L 113.77 -38.4" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-110" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-40.9 L 113.77 -40.9" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-111" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-43.39 L 113.77 -43.39" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-112" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-113" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-114" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-115" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-116" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-117" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M18.63,141.01 L 113.77 141.01" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-118" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,134.78 L 113.77 134.78" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-119" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,128.55 L 113.77 128.55" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-120" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,122.32 L 113.77 122.32" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-121" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,116.09 L 113.77 116.09" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-122" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,109.86 L 113.77 109.86" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-123" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,103.63 L 113.77 103.63" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-124" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,97.4 L 113.77 97.4" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-125" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,91.17 L 113.77 91.17" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-126" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,84.94 L 113.77 84.94" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-127" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,78.72 L 113.77 78.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-128" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,72.49 L 113.77 72.49" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-129" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,66.26 L 113.77 66.26" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-130" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,60.03 L 113.77 60.03" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-131" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,53.8 L 113.77 53.8" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-132" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,47.57 L 113.77 47.57" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-133" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,41.34 L 113.77 41.34" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-134" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,35.11 L 113.77 35.11" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-135" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,28.88 L 113.77 28.88" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-136" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,22.65 L 113.77 22.65" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-137" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,16.42 L 113.77 16.42" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-138" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,10.19 L 113.77 10.19" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-139" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,3.96 L 113.77 3.96" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-140" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-2.27 L 113.77 -2.27" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-141" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-8.5 L 113.77 -8.5" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-142" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-14.73 L 113.77 -14.73" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-143" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-20.96 L 113.77 -20.96" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-144" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-27.19 L 113.77 -27.19" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-145" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-33.42 L 113.77 -33.42" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-146" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-39.65 L 113.77 -39.65" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-147" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M18.63,-45.88 L 113.77 -45.88" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-148" gadfly:scale="5.0" visibility="hidden"/>
    </g>
    <g class="guide xgridlines yfixed" stroke-dasharray="0.5,0.5" stroke-width="0.2" stroke="#D0D0E0" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-149">
      <path fill="none" d="M-93.29,14.42 L -93.29 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-150" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-151" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-47.72,14.42 L -47.72 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-152" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-24.94,14.42 L -24.94 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-153" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-2.15,14.42 L -2.15 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-154" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-155" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M43.42,14.42 L 43.42 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-156" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M66.2,14.42 L 66.2 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-157" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M88.99,14.42 L 88.99 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-158" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-159" gadfly:scale="1.0" visibility="visible"/>
      <path fill="none" d="M134.56,14.42 L 134.56 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-160" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M157.34,14.42 L 157.34 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-161" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M180.12,14.42 L 180.12 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-162" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-163" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M225.69,14.42 L 225.69 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-164" gadfly:scale="1.0" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-165" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-65.95,14.42 L -65.95 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-166" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-61.39,14.42 L -61.39 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-167" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-56.84,14.42 L -56.84 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-168" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-52.28,14.42 L -52.28 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-169" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-47.72,14.42 L -47.72 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-170" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-43.17,14.42 L -43.17 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-171" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-38.61,14.42 L -38.61 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-172" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-34.05,14.42 L -34.05 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-173" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-29.49,14.42 L -29.49 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-174" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-24.94,14.42 L -24.94 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-175" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-20.38,14.42 L -20.38 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-176" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-15.82,14.42 L -15.82 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-177" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-11.27,14.42 L -11.27 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-178" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-6.71,14.42 L -6.71 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-179" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-2.15,14.42 L -2.15 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-180" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M2.4,14.42 L 2.4 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-181" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M6.96,14.42 L 6.96 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-182" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M11.52,14.42 L 11.52 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-183" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M16.07,14.42 L 16.07 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-184" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-185" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M25.19,14.42 L 25.19 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-186" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M29.75,14.42 L 29.75 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-187" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M34.3,14.42 L 34.3 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-188" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M38.86,14.42 L 38.86 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-189" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M43.42,14.42 L 43.42 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-190" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M47.97,14.42 L 47.97 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-191" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M52.53,14.42 L 52.53 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-192" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M57.09,14.42 L 57.09 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-193" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M61.64,14.42 L 61.64 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-194" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M66.2,14.42 L 66.2 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-195" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M70.76,14.42 L 70.76 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-196" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M75.31,14.42 L 75.31 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-197" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M79.87,14.42 L 79.87 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-198" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M84.43,14.42 L 84.43 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-199" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M88.99,14.42 L 88.99 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-200" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M93.54,14.42 L 93.54 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-201" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M98.1,14.42 L 98.1 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-202" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M102.66,14.42 L 102.66 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-203" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M107.21,14.42 L 107.21 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-204" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-205" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M116.33,14.42 L 116.33 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-206" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M120.88,14.42 L 120.88 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-207" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M125.44,14.42 L 125.44 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-208" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M130,14.42 L 130 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-209" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M134.56,14.42 L 134.56 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-210" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M139.11,14.42 L 139.11 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-211" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M143.67,14.42 L 143.67 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-212" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M148.23,14.42 L 148.23 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-213" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M152.78,14.42 L 152.78 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-214" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M157.34,14.42 L 157.34 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-215" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M161.9,14.42 L 161.9 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-216" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M166.45,14.42 L 166.45 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-217" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M171.01,14.42 L 171.01 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-218" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M175.57,14.42 L 175.57 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-219" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M180.12,14.42 L 180.12 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-220" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M184.68,14.42 L 184.68 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-221" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M189.24,14.42 L 189.24 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-222" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M193.8,14.42 L 193.8 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-223" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M198.35,14.42 L 198.35 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-224" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-225" gadfly:scale="10.0" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-226" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-227" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-228" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-229" gadfly:scale="0.5" visibility="hidden"/>
      <path fill="none" d="M-70.51,14.42 L -70.51 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-230" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-61.39,14.42 L -61.39 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-231" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-52.28,14.42 L -52.28 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-232" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-43.17,14.42 L -43.17 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-233" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-34.05,14.42 L -34.05 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-234" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-24.94,14.42 L -24.94 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-235" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-15.82,14.42 L -15.82 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-236" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M-6.71,14.42 L -6.71 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-237" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M2.4,14.42 L 2.4 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-238" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M11.52,14.42 L 11.52 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-239" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M20.63,14.42 L 20.63 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-240" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M29.75,14.42 L 29.75 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-241" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M38.86,14.42 L 38.86 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-242" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M47.97,14.42 L 47.97 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-243" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M57.09,14.42 L 57.09 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-244" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M66.2,14.42 L 66.2 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-245" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M75.31,14.42 L 75.31 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-246" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M84.43,14.42 L 84.43 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-247" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M93.54,14.42 L 93.54 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-248" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M102.66,14.42 L 102.66 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-249" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M111.77,14.42 L 111.77 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-250" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M120.88,14.42 L 120.88 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-251" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M130,14.42 L 130 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-252" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M139.11,14.42 L 139.11 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-253" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M148.23,14.42 L 148.23 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-254" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M157.34,14.42 L 157.34 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-255" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M166.45,14.42 L 166.45 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-256" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M175.57,14.42 L 175.57 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-257" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M184.68,14.42 L 184.68 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-258" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M193.8,14.42 L 193.8 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-259" gadfly:scale="5.0" visibility="hidden"/>
      <path fill="none" d="M202.91,14.42 L 202.91 80.72" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-260" gadfly:scale="5.0" visibility="hidden"/>
    </g>
    <g class="plotpanel" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-261">
      <g stroke-width="0.3" fill="none" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-262">
        <path fill="none" d="M20.63,78.72 L 21 77.72 21.36 76.75 21.73 75.78 22.1 74.84 22.46 73.91 22.83 72.99 23.19 72.09 23.56 71.2 23.93 70.33 24.29 69.47 24.66 68.62 25.02 67.79 25.39 66.97 25.76 66.17 26.12 65.38 26.49 64.6 26.85 63.83 27.22 63.07 27.59 62.33 27.95 61.6 28.32 60.88 28.68 60.17 29.05 59.47 29.42 58.78 29.78 58.11 30.15 57.45 30.51 56.79 30.88 56.15 31.25 55.51 31.61 54.89 31.98 54.28 32.34 53.68 32.71 53.08 33.08 52.5 33.44 51.92 33.81 51.36 34.17 50.8 34.54 50.25 34.91 49.71 35.27 49.18 35.64 48.66 36 48.15 36.37 47.64 36.74 47.14 37.1 46.65 37.47 46.17 37.83 45.7 38.2 45.23 38.57 44.77 38.93 44.32 39.3 43.88 39.66 43.44 40.03 43.01 40.4 42.58 40.76 42.17 41.13 41.76 41.49 41.35 41.86 40.95 42.23 40.56 42.59 40.18 42.96 39.8 43.32 39.43 43.69 39.06 44.06 38.7 44.42 38.35 44.79 38 45.15 37.65 45.52 37.31 45.89 36.98 46.25 36.65 46.62 36.33 46.99 36.01 47.35 35.7 47.72 35.39 48.08 35.09 48.45 34.79 48.82 34.5 49.18 34.21 49.55 33.93 49.91 33.65 50.28 33.38 50.65 33.1 51.01 32.84 51.38 32.58 51.74 32.32 52.11 32.07 52.48 31.82 52.84 31.57 53.21 31.33 53.57 31.09 53.94 30.86 54.31 30.63 54.67 30.4 55.04 30.18 55.4 29.96 55.77 29.74 56.14 29.53 56.5 29.32 56.87 29.12 57.23 28.91 57.6 28.72 57.97 28.52 58.33 28.33 58.7 28.14 59.06 27.95 59.43 27.77 59.8 27.59 60.16 27.41 60.53 27.23 60.89 27.06 61.26 26.89 61.63 26.72 61.99 26.56 62.36 26.4 62.72 26.24 63.09 26.08 63.46 25.93 63.82 25.78 64.19 25.63 64.55 25.48 64.92 25.34 65.29 25.19 65.65 25.05 66.02 24.92 66.38 24.78 66.75 24.65 67.12 24.52 67.48 24.39 67.85 24.26 68.21 24.14 68.58 24.01 68.95 23.89 69.31 23.77 69.68 23.66 70.04 23.54 70.41 23.43 70.78 23.31 71.14 23.2 71.51 23.1 71.87 22.99 72.24 22.89 72.61 22.78 72.97 22.68 73.34 22.58 73.7 22.48 74.07 22.39 74.44 22.29 74.8 22.2 75.17 22.11 75.53 22.01 75.9 21.93 76.27 21.84 76.63 21.75 77 21.67 77.36 21.58 77.73 21.5 78.1 21.42 78.46 21.34 78.83 21.26 79.19 21.18 79.56 21.11 79.93 21.03 80.29 20.96 80.66 20.89 81.02 20.82 81.39 20.75 81.76 20.68 82.12 20.61 82.49 20.54 82.85 20.48 83.22 20.41 83.59 20.35 83.95 20.29 84.32 20.22 84.69 20.16 85.05 20.1 85.42 20.05 85.78 19.99 86.15 19.93 86.52 19.87 86.88 19.82 87.25 19.77 87.61 19.71 87.98 19.66 88.35 19.61 88.71 19.56 89.08 19.51 89.44 19.46 89.81 19.41 90.18 19.36 90.54 19.31 90.91 19.27 91.27 19.22 91.64 19.18 92.01 19.13 92.37 19.09 92.74 19.05 93.1 19.01 93.47 18.97 93.84 18.92 94.2 18.88 94.57 18.85 94.93 18.81 95.3 18.77 95.67 18.73 96.03 18.69 96.4 18.66 96.76 18.62 97.13 18.59 97.5 18.55 97.86 18.52 98.23 18.48 98.59 18.45 98.96 18.42 99.33 18.39 99.69 18.36 100.06 18.33 100.42 18.29 100.79 18.27 101.16 18.24 101.52 18.21 101.89 18.18 102.25 18.15 102.62 18.12 102.99 18.1 103.35 18.07 103.72 18.04 104.08 18.02 104.45 17.99 104.82 17.97 105.18 17.94 105.55 17.92 105.91 17.89 106.28 17.87 106.65 17.85 107.01 17.82 107.38 17.8 107.74 17.78 108.11 17.76 108.48 17.74 108.84 17.71 109.21 17.69 109.57 17.67 109.94 17.65 110.31 17.63 110.67 17.61 111.04 17.6 111.4 17.58 111.77 17.56" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-263" stroke="#D4CA3A" class="geometry color_f2"/>
        <path fill="none" d="M20.63,78.72 L 21 77.71 21.36 76.71 21.73 75.72 22.1 74.72 22.46 73.72 22.83 72.73 23.19 71.74 23.56 70.75 23.93 69.77 24.29 68.79 24.66 67.82 25.02 66.85 25.39 65.89 25.76 64.94 26.12 63.99 26.49 63.05 26.85 62.11 27.22 61.19 27.59 60.27 27.95 59.36 28.32 58.46 28.68 57.57 29.05 56.69 29.42 55.82 29.78 54.96 30.15 54.11 30.51 53.27 30.88 52.44 31.25 51.62 31.61 50.82 31.98 50.02 32.34 49.24 32.71 48.47 33.08 47.71 33.44 46.97 33.81 46.23 34.17 45.51 34.54 44.8 34.91 44.1 35.27 43.41 35.64 42.74 36 42.08 36.37 41.43 36.74 40.8 37.1 40.17 37.47 39.56 37.83 38.96 38.2 38.37 38.57 37.8 38.93 37.24 39.3 36.68 39.66 36.15 40.03 35.62 40.4 35.1 40.76 34.6 41.13 34.1 41.49 33.62 41.86 33.15 42.23 32.69 42.59 32.24 42.96 31.8 43.32 31.37 43.69 30.96 44.06 30.55 44.42 30.15 44.79 29.76 45.15 29.39 45.52 29.02 45.89 28.66 46.25 28.31 46.62 27.97 46.99 27.63 47.35 27.31 47.72 27 48.08 26.69 48.45 26.39 48.82 26.1 49.18 25.82 49.55 25.54 49.91 25.27 50.28 25.01 50.65 24.76 51.01 24.51 51.38 24.27 51.74 24.04 52.11 23.81 52.48 23.59 52.84 23.38 53.21 23.17 53.57 22.97 53.94 22.77 54.31 22.58 54.67 22.39 55.04 22.21 55.4 22.04 55.77 21.87 56.14 21.7 56.5 21.54 56.87 21.39 57.23 21.24 57.6 21.09 57.97 20.95 58.33 20.81 58.7 20.68 59.06 20.55 59.43 20.42 59.8 20.3 60.16 20.18 60.53 20.06 60.89 19.95 61.26 19.84 61.63 19.74 61.99 19.63 62.36 19.54 62.72 19.44 63.09 19.35 63.46 19.26 63.82 19.17 64.19 19.08 64.55 19 64.92 18.92 65.29 18.84 65.65 18.77 66.02 18.69 66.38 18.62 66.75 18.55 67.12 18.49 67.48 18.42 67.85 18.36 68.21 18.3 68.58 18.24 68.95 18.19 69.31 18.13 69.68 18.08 70.04 18.03 70.41 17.97 70.78 17.93 71.14 17.88 71.51 17.83 71.87 17.79 72.24 17.75 72.61 17.7 72.97 17.66 73.34 17.63 73.7 17.59 74.07 17.55 74.44 17.52 74.8 17.48 75.17 17.45 75.53 17.42 75.9 17.38 76.27 17.35 76.63 17.32 77 17.3 77.36 17.27 77.73 17.24 78.1 17.22 78.46 17.19 78.83 17.17 79.19 17.14 79.56 17.12 79.93 17.1 80.29 17.08 80.66 17.06 81.02 17.04 81.39 17.02 81.76 17 82.12 16.98 82.49 16.96 82.85 16.94 83.22 16.93 83.59 16.91 83.95 16.9 84.32 16.88 84.69 16.87 85.05 16.85 85.42 16.84 85.78 16.83 86.15 16.81 86.52 16.8 86.88 16.79 87.25 16.78 87.61 16.76 87.98 16.75 88.35 16.74 88.71 16.73 89.08 16.72 89.44 16.71 89.81 16.7 90.18 16.7 90.54 16.69 90.91 16.68 91.27 16.67 91.64 16.66 92.01 16.65 92.37 16.65 92.74 16.64 93.1 16.63 93.47 16.63 93.84 16.62 94.2 16.61 94.57 16.61 94.93 16.6 95.3 16.59 95.67 16.59 96.03 16.58 96.4 16.58 96.76 16.57 97.13 16.57 97.5 16.56 97.86 16.56 98.23 16.55 98.59 16.55 98.96 16.55 99.33 16.54 99.69 16.54 100.06 16.53 100.42 16.53 100.79 16.53 101.16 16.52 101.52 16.52 101.89 16.52 102.25 16.51 102.62 16.51 102.99 16.51 103.35 16.5 103.72 16.5 104.08 16.5 104.45 16.5 104.82 16.49 105.18 16.49 105.55 16.49 105.91 16.49 106.28 16.49 106.65 16.48 107.01 16.48 107.38 16.48 107.74 16.48 108.11 16.48 108.48 16.47 108.84 16.47 109.21 16.47 109.57 16.47 109.94 16.47 110.31 16.47 110.67 16.46 111.04 16.46 111.4 16.46 111.77 16.46" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-264" stroke="#FF5EA0" class="geometry color_f3"/>
        <path fill="none" d="M20.63,78.72 L 21 77.72 21.36 76.74 21.73 75.77 22.1 74.82 22.46 73.88 22.83 72.95 23.19 72.03 23.56 71.13 23.93 70.23 24.29 69.35 24.66 68.49 25.02 67.63 25.39 66.79 25.76 65.95 26.12 65.13 26.49 64.32 26.85 63.52 27.22 62.74 27.59 61.96 27.95 61.2 28.32 60.44 28.68 59.7 29.05 58.96 29.42 58.24 29.78 57.53 30.15 56.82 30.51 56.13 30.88 55.45 31.25 54.78 31.61 54.11 31.98 53.46 32.34 52.81 32.71 52.18 33.08 51.55 33.44 50.94 33.81 50.33 34.17 49.73 34.54 49.14 34.91 48.56 35.27 47.99 35.64 47.43 36 46.87 36.37 46.32 36.74 45.78 37.1 45.25 37.47 44.73 37.83 44.22 38.2 43.71 38.57 43.21 38.93 42.72 39.3 42.23 39.66 41.76 40.03 41.29 40.4 40.83 40.76 40.37 41.13 39.92 41.49 39.48 41.86 39.05 42.23 38.62 42.59 38.2 42.96 37.79 43.32 37.38 43.69 36.98 44.06 36.59 44.42 36.2 44.79 35.82 45.15 35.44 45.52 35.07 45.89 34.71 46.25 34.35 46.62 34 46.99 33.65 47.35 33.31 47.72 32.98 48.08 32.65 48.45 32.33 48.82 32.01 49.18 31.7 49.55 31.39 49.91 31.09 50.28 30.79 50.65 30.5 51.01 30.21 51.38 29.93 51.74 29.65 52.11 29.38 52.48 29.11 52.84 28.84 53.21 28.59 53.57 28.33 53.94 28.08 54.31 27.84 54.67 27.59 55.04 27.36 55.4 27.12 55.77 26.9 56.14 26.67 56.5 26.45 56.87 26.23 57.23 26.02 57.6 25.81 57.97 25.61 58.33 25.41 58.7 25.21 59.06 25.02 59.43 24.83 59.8 24.64 60.16 24.45 60.53 24.27 60.89 24.1 61.26 23.93 61.63 23.76 61.99 23.59 62.36 23.42 62.72 23.26 63.09 23.11 63.46 22.95 63.82 22.8 64.19 22.65 64.55 22.51 64.92 22.36 65.29 22.22 65.65 22.09 66.02 21.95 66.38 21.82 66.75 21.69 67.12 21.57 67.48 21.44 67.85 21.32 68.21 21.2 68.58 21.08 68.95 20.97 69.31 20.86 69.68 20.75 70.04 20.64 70.41 20.54 70.78 20.43 71.14 20.33 71.51 20.23 71.87 20.14 72.24 20.04 72.61 19.95 72.97 19.86 73.34 19.77 73.7 19.68 74.07 19.6 74.44 19.52 74.8 19.43 75.17 19.36 75.53 19.28 75.9 19.2 76.27 19.13 76.63 19.05 77 18.98 77.36 18.91 77.73 18.85 78.1 18.78 78.46 18.72 78.83 18.65 79.19 18.59 79.56 18.53 79.93 18.47 80.29 18.41 80.66 18.36 81.02 18.3 81.39 18.25 81.76 18.2 82.12 18.15 82.49 18.1 82.85 18.05 83.22 18 83.59 17.95 83.95 17.91 84.32 17.86 84.69 17.82 85.05 17.78 85.42 17.74 85.78 17.7 86.15 17.66 86.52 17.62 86.88 17.59 87.25 17.55 87.61 17.51 87.98 17.48 88.35 17.45 88.71 17.41 89.08 17.38 89.44 17.35 89.81 17.32 90.18 17.29 90.54 17.27 90.91 17.24 91.27 17.21 91.64 17.19 92.01 17.16 92.37 17.14 92.74 17.11 93.1 17.09 93.47 17.07 93.84 17.04 94.2 17.02 94.57 17 94.93 16.98 95.3 16.96 95.67 16.94 96.03 16.92 96.4 16.91 96.76 16.89 97.13 16.87 97.5 16.86 97.86 16.84 98.23 16.82 98.59 16.81 98.96 16.8 99.33 16.78 99.69 16.77 100.06 16.75 100.42 16.74 100.79 16.73 101.16 16.72 101.52 16.71 101.89 16.69 102.25 16.68 102.62 16.67 102.99 16.66 103.35 16.65 103.72 16.64 104.08 16.64 104.45 16.63 104.82 16.62 105.18 16.61 105.55 16.6 105.91 16.59 106.28 16.59 106.65 16.58 107.01 16.57 107.38 16.57 107.74 16.56 108.11 16.55 108.48 16.55 108.84 16.54 109.21 16.54 109.57 16.53 109.94 16.53 110.31 16.52 110.67 16.52 111.04 16.51 111.4 16.51 111.77 16.5" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-265" stroke="#00BFFF" class="geometry color_f1"/>
      </g>
    </g>
    <g opacity="0" class="guide zoomslider" stroke="none" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-266">
      <g fill="#EAEAEA" stroke-width="0.3" stroke-opacity="0" stroke="#6A6A6A" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-267">
        <rect x="106.77" y="17.42" width="4" height="4" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-268"/>
        <g class="button_logo" fill="#6A6A6A" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-269">
          <path d="M107.57,19.02 L 108.37 19.02 108.37 18.22 109.17 18.22 109.17 19.02 109.97 19.02 109.97 19.82 109.17 19.82 109.17 20.62 108.37 20.62 108.37 19.82 107.57 19.82 z" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-270"/>
        </g>
      </g>
      <g fill="#EAEAEA" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-271">
        <rect x="87.27" y="17.42" width="19" height="4" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-272"/>
      </g>
      <g class="zoomslider_thumb" fill="#6A6A6A" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-273">
        <rect x="95.77" y="17.42" width="2" height="4" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-274"/>
      </g>
      <g fill="#EAEAEA" stroke-width="0.3" stroke-opacity="0" stroke="#6A6A6A" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-275">
        <rect x="82.77" y="17.42" width="4" height="4" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-276"/>
        <g class="button_logo" fill="#6A6A6A" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-277">
          <path d="M83.57,19.02 L 85.97 19.02 85.97 19.82 83.57 19.82 z" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-278"/>
        </g>
      </g>
    </g>
  </g>
  <g class="guide ylabels" font-size="2.82" font-family="'PT Sans Caption','Helvetica Neue','Helvetica',sans-serif" fill="#6C606B" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-279">
    <text x="17.63" y="153.47" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-280" gadfly:scale="1.0" visibility="hidden">-0.6</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-281" gadfly:scale="1.0" visibility="hidden">-0.5</text>
    <text x="17.63" y="128.55" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-282" gadfly:scale="1.0" visibility="hidden">-0.4</text>
    <text x="17.63" y="116.09" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-283" gadfly:scale="1.0" visibility="hidden">-0.3</text>
    <text x="17.63" y="103.63" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-284" gadfly:scale="1.0" visibility="hidden">-0.2</text>
    <text x="17.63" y="91.17" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-285" gadfly:scale="1.0" visibility="hidden">-0.1</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-286" gadfly:scale="1.0" visibility="visible">0.0</text>
    <text x="17.63" y="66.26" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-287" gadfly:scale="1.0" visibility="visible">0.1</text>
    <text x="17.63" y="53.8" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-288" gadfly:scale="1.0" visibility="visible">0.2</text>
    <text x="17.63" y="41.34" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-289" gadfly:scale="1.0" visibility="visible">0.3</text>
    <text x="17.63" y="28.88" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-290" gadfly:scale="1.0" visibility="visible">0.4</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-291" gadfly:scale="1.0" visibility="visible">0.5</text>
    <text x="17.63" y="3.96" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-292" gadfly:scale="1.0" visibility="hidden">0.6</text>
    <text x="17.63" y="-8.5" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-293" gadfly:scale="1.0" visibility="hidden">0.7</text>
    <text x="17.63" y="-20.96" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-294" gadfly:scale="1.0" visibility="hidden">0.8</text>
    <text x="17.63" y="-33.42" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-295" gadfly:scale="1.0" visibility="hidden">0.9</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-296" gadfly:scale="1.0" visibility="hidden">1.0</text>
    <text x="17.63" y="-58.34" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-297" gadfly:scale="1.0" visibility="hidden">1.1</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-298" gadfly:scale="10.0" visibility="hidden">-0.50</text>
    <text x="17.63" y="138.52" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-299" gadfly:scale="10.0" visibility="hidden">-0.48</text>
    <text x="17.63" y="136.03" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-300" gadfly:scale="10.0" visibility="hidden">-0.46</text>
    <text x="17.63" y="133.54" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-301" gadfly:scale="10.0" visibility="hidden">-0.44</text>
    <text x="17.63" y="131.04" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-302" gadfly:scale="10.0" visibility="hidden">-0.42</text>
    <text x="17.63" y="128.55" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-303" gadfly:scale="10.0" visibility="hidden">-0.40</text>
    <text x="17.63" y="126.06" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-304" gadfly:scale="10.0" visibility="hidden">-0.38</text>
    <text x="17.63" y="123.57" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-305" gadfly:scale="10.0" visibility="hidden">-0.36</text>
    <text x="17.63" y="121.08" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-306" gadfly:scale="10.0" visibility="hidden">-0.34</text>
    <text x="17.63" y="118.59" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-307" gadfly:scale="10.0" visibility="hidden">-0.32</text>
    <text x="17.63" y="116.09" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-308" gadfly:scale="10.0" visibility="hidden">-0.30</text>
    <text x="17.63" y="113.6" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-309" gadfly:scale="10.0" visibility="hidden">-0.28</text>
    <text x="17.63" y="111.11" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-310" gadfly:scale="10.0" visibility="hidden">-0.26</text>
    <text x="17.63" y="108.62" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-311" gadfly:scale="10.0" visibility="hidden">-0.24</text>
    <text x="17.63" y="106.13" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-312" gadfly:scale="10.0" visibility="hidden">-0.22</text>
    <text x="17.63" y="103.63" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-313" gadfly:scale="10.0" visibility="hidden">-0.20</text>
    <text x="17.63" y="101.14" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-314" gadfly:scale="10.0" visibility="hidden">-0.18</text>
    <text x="17.63" y="98.65" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-315" gadfly:scale="10.0" visibility="hidden">-0.16</text>
    <text x="17.63" y="96.16" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-316" gadfly:scale="10.0" visibility="hidden">-0.14</text>
    <text x="17.63" y="93.67" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-317" gadfly:scale="10.0" visibility="hidden">-0.12</text>
    <text x="17.63" y="91.17" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-318" gadfly:scale="10.0" visibility="hidden">-0.10</text>
    <text x="17.63" y="88.68" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-319" gadfly:scale="10.0" visibility="hidden">-0.08</text>
    <text x="17.63" y="86.19" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-320" gadfly:scale="10.0" visibility="hidden">-0.06</text>
    <text x="17.63" y="83.7" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-321" gadfly:scale="10.0" visibility="hidden">-0.04</text>
    <text x="17.63" y="81.21" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-322" gadfly:scale="10.0" visibility="hidden">-0.02</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-323" gadfly:scale="10.0" visibility="hidden">0.00</text>
    <text x="17.63" y="76.22" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-324" gadfly:scale="10.0" visibility="hidden">0.02</text>
    <text x="17.63" y="73.73" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-325" gadfly:scale="10.0" visibility="hidden">0.04</text>
    <text x="17.63" y="71.24" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-326" gadfly:scale="10.0" visibility="hidden">0.06</text>
    <text x="17.63" y="68.75" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-327" gadfly:scale="10.0" visibility="hidden">0.08</text>
    <text x="17.63" y="66.26" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-328" gadfly:scale="10.0" visibility="hidden">0.10</text>
    <text x="17.63" y="63.76" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-329" gadfly:scale="10.0" visibility="hidden">0.12</text>
    <text x="17.63" y="61.27" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-330" gadfly:scale="10.0" visibility="hidden">0.14</text>
    <text x="17.63" y="58.78" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-331" gadfly:scale="10.0" visibility="hidden">0.16</text>
    <text x="17.63" y="56.29" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-332" gadfly:scale="10.0" visibility="hidden">0.18</text>
    <text x="17.63" y="53.8" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-333" gadfly:scale="10.0" visibility="hidden">0.20</text>
    <text x="17.63" y="51.3" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-334" gadfly:scale="10.0" visibility="hidden">0.22</text>
    <text x="17.63" y="48.81" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-335" gadfly:scale="10.0" visibility="hidden">0.24</text>
    <text x="17.63" y="46.32" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-336" gadfly:scale="10.0" visibility="hidden">0.26</text>
    <text x="17.63" y="43.83" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-337" gadfly:scale="10.0" visibility="hidden">0.28</text>
    <text x="17.63" y="41.34" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-338" gadfly:scale="10.0" visibility="hidden">0.30</text>
    <text x="17.63" y="38.84" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-339" gadfly:scale="10.0" visibility="hidden">0.32</text>
    <text x="17.63" y="36.35" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-340" gadfly:scale="10.0" visibility="hidden">0.34</text>
    <text x="17.63" y="33.86" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-341" gadfly:scale="10.0" visibility="hidden">0.36</text>
    <text x="17.63" y="31.37" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-342" gadfly:scale="10.0" visibility="hidden">0.38</text>
    <text x="17.63" y="28.88" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-343" gadfly:scale="10.0" visibility="hidden">0.40</text>
    <text x="17.63" y="26.39" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-344" gadfly:scale="10.0" visibility="hidden">0.42</text>
    <text x="17.63" y="23.89" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-345" gadfly:scale="10.0" visibility="hidden">0.44</text>
    <text x="17.63" y="21.4" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-346" gadfly:scale="10.0" visibility="hidden">0.46</text>
    <text x="17.63" y="18.91" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-347" gadfly:scale="10.0" visibility="hidden">0.48</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-348" gadfly:scale="10.0" visibility="hidden">0.50</text>
    <text x="17.63" y="13.93" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-349" gadfly:scale="10.0" visibility="hidden">0.52</text>
    <text x="17.63" y="11.43" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-350" gadfly:scale="10.0" visibility="hidden">0.54</text>
    <text x="17.63" y="8.94" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-351" gadfly:scale="10.0" visibility="hidden">0.56</text>
    <text x="17.63" y="6.45" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-352" gadfly:scale="10.0" visibility="hidden">0.58</text>
    <text x="17.63" y="3.96" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-353" gadfly:scale="10.0" visibility="hidden">0.60</text>
    <text x="17.63" y="1.47" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-354" gadfly:scale="10.0" visibility="hidden">0.62</text>
    <text x="17.63" y="-1.03" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-355" gadfly:scale="10.0" visibility="hidden">0.64</text>
    <text x="17.63" y="-3.52" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-356" gadfly:scale="10.0" visibility="hidden">0.66</text>
    <text x="17.63" y="-6.01" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-357" gadfly:scale="10.0" visibility="hidden">0.68</text>
    <text x="17.63" y="-8.5" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-358" gadfly:scale="10.0" visibility="hidden">0.70</text>
    <text x="17.63" y="-10.99" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-359" gadfly:scale="10.0" visibility="hidden">0.72</text>
    <text x="17.63" y="-13.49" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-360" gadfly:scale="10.0" visibility="hidden">0.74</text>
    <text x="17.63" y="-15.98" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-361" gadfly:scale="10.0" visibility="hidden">0.76</text>
    <text x="17.63" y="-18.47" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-362" gadfly:scale="10.0" visibility="hidden">0.78</text>
    <text x="17.63" y="-20.96" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-363" gadfly:scale="10.0" visibility="hidden">0.80</text>
    <text x="17.63" y="-23.45" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-364" gadfly:scale="10.0" visibility="hidden">0.82</text>
    <text x="17.63" y="-25.94" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-365" gadfly:scale="10.0" visibility="hidden">0.84</text>
    <text x="17.63" y="-28.44" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-366" gadfly:scale="10.0" visibility="hidden">0.86</text>
    <text x="17.63" y="-30.93" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-367" gadfly:scale="10.0" visibility="hidden">0.88</text>
    <text x="17.63" y="-33.42" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-368" gadfly:scale="10.0" visibility="hidden">0.90</text>
    <text x="17.63" y="-35.91" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-369" gadfly:scale="10.0" visibility="hidden">0.92</text>
    <text x="17.63" y="-38.4" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-370" gadfly:scale="10.0" visibility="hidden">0.94</text>
    <text x="17.63" y="-40.9" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-371" gadfly:scale="10.0" visibility="hidden">0.96</text>
    <text x="17.63" y="-43.39" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-372" gadfly:scale="10.0" visibility="hidden">0.98</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-373" gadfly:scale="10.0" visibility="hidden">1.00</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-374" gadfly:scale="0.5" visibility="hidden">-0.5</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-375" gadfly:scale="0.5" visibility="hidden">0.0</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-376" gadfly:scale="0.5" visibility="hidden">0.5</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-377" gadfly:scale="0.5" visibility="hidden">1.0</text>
    <text x="17.63" y="141.01" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-378" gadfly:scale="5.0" visibility="hidden">-0.50</text>
    <text x="17.63" y="134.78" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-379" gadfly:scale="5.0" visibility="hidden">-0.45</text>
    <text x="17.63" y="128.55" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-380" gadfly:scale="5.0" visibility="hidden">-0.40</text>
    <text x="17.63" y="122.32" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-381" gadfly:scale="5.0" visibility="hidden">-0.35</text>
    <text x="17.63" y="116.09" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-382" gadfly:scale="5.0" visibility="hidden">-0.30</text>
    <text x="17.63" y="109.86" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-383" gadfly:scale="5.0" visibility="hidden">-0.25</text>
    <text x="17.63" y="103.63" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-384" gadfly:scale="5.0" visibility="hidden">-0.20</text>
    <text x="17.63" y="97.4" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-385" gadfly:scale="5.0" visibility="hidden">-0.15</text>
    <text x="17.63" y="91.17" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-386" gadfly:scale="5.0" visibility="hidden">-0.10</text>
    <text x="17.63" y="84.94" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-387" gadfly:scale="5.0" visibility="hidden">-0.05</text>
    <text x="17.63" y="78.72" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-388" gadfly:scale="5.0" visibility="hidden">0.00</text>
    <text x="17.63" y="72.49" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-389" gadfly:scale="5.0" visibility="hidden">0.05</text>
    <text x="17.63" y="66.26" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-390" gadfly:scale="5.0" visibility="hidden">0.10</text>
    <text x="17.63" y="60.03" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-391" gadfly:scale="5.0" visibility="hidden">0.15</text>
    <text x="17.63" y="53.8" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-392" gadfly:scale="5.0" visibility="hidden">0.20</text>
    <text x="17.63" y="47.57" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-393" gadfly:scale="5.0" visibility="hidden">0.25</text>
    <text x="17.63" y="41.34" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-394" gadfly:scale="5.0" visibility="hidden">0.30</text>
    <text x="17.63" y="35.11" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-395" gadfly:scale="5.0" visibility="hidden">0.35</text>
    <text x="17.63" y="28.88" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-396" gadfly:scale="5.0" visibility="hidden">0.40</text>
    <text x="17.63" y="22.65" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-397" gadfly:scale="5.0" visibility="hidden">0.45</text>
    <text x="17.63" y="16.42" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-398" gadfly:scale="5.0" visibility="hidden">0.50</text>
    <text x="17.63" y="10.19" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-399" gadfly:scale="5.0" visibility="hidden">0.55</text>
    <text x="17.63" y="3.96" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-400" gadfly:scale="5.0" visibility="hidden">0.60</text>
    <text x="17.63" y="-2.27" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-401" gadfly:scale="5.0" visibility="hidden">0.65</text>
    <text x="17.63" y="-8.5" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-402" gadfly:scale="5.0" visibility="hidden">0.70</text>
    <text x="17.63" y="-14.73" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-403" gadfly:scale="5.0" visibility="hidden">0.75</text>
    <text x="17.63" y="-20.96" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-404" gadfly:scale="5.0" visibility="hidden">0.80</text>
    <text x="17.63" y="-27.19" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-405" gadfly:scale="5.0" visibility="hidden">0.85</text>
    <text x="17.63" y="-33.42" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-406" gadfly:scale="5.0" visibility="hidden">0.90</text>
    <text x="17.63" y="-39.65" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-407" gadfly:scale="5.0" visibility="hidden">0.95</text>
    <text x="17.63" y="-45.88" text-anchor="end" dy="0.35em" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-408" gadfly:scale="5.0" visibility="hidden">1.00</text>
  </g>
  <g font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" fill="#564A55" stroke="none" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-409">
    <text x="8.81" y="45.57" text-anchor="middle" dy="0.35em" transform="rotate(-90, 8.81, 47.57)" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-410">Recombination Rate</text>
  </g>
  <g font-size="3.88" font-family="'PT Sans','Helvetica Neue','Helvetica',sans-serif" fill="#564A55" stroke="none" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-411">
    <text x="66.2" y="12.42" text-anchor="middle" id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-412">Karlin's (f<tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">1</tspan><tspan dy="-0.498000em">), Haldane's (f</tspan><tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">2</tspan><tspan dy="-0.498000em">) and Kosambi's (f</tspan><tspan style="dominant-baseline:inherit" dy="0.6em" font-size="83%">3</tspan><tspan dy="-0.498000em">)  Map Functions</tspan></text>
  </g>
</g>
<defs>
<clipPath id="fig-8226a61cd72e412e8cc8f049f5a87d42-element-16">
  <path d="M18.63,14.42 L 113.77 14.42 113.77 80.72 18.63 80.72" />
</clipPath
></defs>
<script> <![CDATA[
(function(N){var k=/[\.\/]/,L=/\s*,\s*/,C=function(a,d){return a-d},a,v,y={n:{}},M=function(){for(var a=0,d=this.length;a<d;a++)if("undefined"!=typeof this[a])return this[a]},A=function(){for(var a=this.length;--a;)if("undefined"!=typeof this[a])return this[a]},w=function(k,d){k=String(k);var f=v,n=Array.prototype.slice.call(arguments,2),u=w.listeners(k),p=0,b,q=[],e={},l=[],r=a;l.firstDefined=M;l.lastDefined=A;a=k;for(var s=v=0,x=u.length;s<x;s++)"zIndex"in u[s]&&(q.push(u[s].zIndex),0>u[s].zIndex&&
(e[u[s].zIndex]=u[s]));for(q.sort(C);0>q[p];)if(b=e[q[p++] ],l.push(b.apply(d,n)),v)return v=f,l;for(s=0;s<x;s++)if(b=u[s],"zIndex"in b)if(b.zIndex==q[p]){l.push(b.apply(d,n));if(v)break;do if(p++,(b=e[q[p] ])&&l.push(b.apply(d,n)),v)break;while(b)}else e[b.zIndex]=b;else if(l.push(b.apply(d,n)),v)break;v=f;a=r;return l};w._events=y;w.listeners=function(a){a=a.split(k);var d=y,f,n,u,p,b,q,e,l=[d],r=[];u=0;for(p=a.length;u<p;u++){e=[];b=0;for(q=l.length;b<q;b++)for(d=l[b].n,f=[d[a[u] ],d["*"] ],n=2;n--;)if(d=
f[n])e.push(d),r=r.concat(d.f||[]);l=e}return r};w.on=function(a,d){a=String(a);if("function"!=typeof d)return function(){};for(var f=a.split(L),n=0,u=f.length;n<u;n++)(function(a){a=a.split(k);for(var b=y,f,e=0,l=a.length;e<l;e++)b=b.n,b=b.hasOwnProperty(a[e])&&b[a[e] ]||(b[a[e] ]={n:{}});b.f=b.f||[];e=0;for(l=b.f.length;e<l;e++)if(b.f[e]==d){f=!0;break}!f&&b.f.push(d)})(f[n]);return function(a){+a==+a&&(d.zIndex=+a)}};w.f=function(a){var d=[].slice.call(arguments,1);return function(){w.apply(null,
[a,null].concat(d).concat([].slice.call(arguments,0)))}};w.stop=function(){v=1};w.nt=function(k){return k?(new RegExp("(?:\\.|\\/|^)"+k+"(?:\\.|\\/|$)")).test(a):a};w.nts=function(){return a.split(k)};w.off=w.unbind=function(a,d){if(a){var f=a.split(L);if(1<f.length)for(var n=0,u=f.length;n<u;n++)w.off(f[n],d);else{for(var f=a.split(k),p,b,q,e,l=[y],n=0,u=f.length;n<u;n++)for(e=0;e<l.length;e+=q.length-2){q=[e,1];p=l[e].n;if("*"!=f[n])p[f[n] ]&&q.push(p[f[n] ]);else for(b in p)p.hasOwnProperty(b)&&
q.push(p[b]);l.splice.apply(l,q)}n=0;for(u=l.length;n<u;n++)for(p=l[n];p.n;){if(d){if(p.f){e=0;for(f=p.f.length;e<f;e++)if(p.f[e]==d){p.f.splice(e,1);break}!p.f.length&&delete p.f}for(b in p.n)if(p.n.hasOwnProperty(b)&&p.n[b].f){q=p.n[b].f;e=0;for(f=q.length;e<f;e++)if(q[e]==d){q.splice(e,1);break}!q.length&&delete p.n[b].f}}else for(b in delete p.f,p.n)p.n.hasOwnProperty(b)&&p.n[b].f&&delete p.n[b].f;p=p.n}}}else w._events=y={n:{}}};w.once=function(a,d){var f=function(){w.unbind(a,f);return d.apply(this,
arguments)};return w.on(a,f)};w.version="0.4.2";w.toString=function(){return"You are running Eve 0.4.2"};"undefined"!=typeof module&&module.exports?module.exports=w:"function"===typeof define&&define.amd?define("eve",[],function(){return w}):N.eve=w})(this);
(function(N,k){"function"===typeof define&&define.amd?define("Snap.svg",["eve"],function(L){return k(N,L)}):k(N,N.eve)})(this,function(N,k){var L=function(a){var k={},y=N.requestAnimationFrame||N.webkitRequestAnimationFrame||N.mozRequestAnimationFrame||N.oRequestAnimationFrame||N.msRequestAnimationFrame||function(a){setTimeout(a,16)},M=Array.isArray||function(a){return a instanceof Array||"[object Array]"==Object.prototype.toString.call(a)},A=0,w="M"+(+new Date).toString(36),z=function(a){if(null==
a)return this.s;var b=this.s-a;this.b+=this.dur*b;this.B+=this.dur*b;this.s=a},d=function(a){if(null==a)return this.spd;this.spd=a},f=function(a){if(null==a)return this.dur;this.s=this.s*a/this.dur;this.dur=a},n=function(){delete k[this.id];this.update();a("mina.stop."+this.id,this)},u=function(){this.pdif||(delete k[this.id],this.update(),this.pdif=this.get()-this.b)},p=function(){this.pdif&&(this.b=this.get()-this.pdif,delete this.pdif,k[this.id]=this)},b=function(){var a;if(M(this.start)){a=[];
for(var b=0,e=this.start.length;b<e;b++)a[b]=+this.start[b]+(this.end[b]-this.start[b])*this.easing(this.s)}else a=+this.start+(this.end-this.start)*this.easing(this.s);this.set(a)},q=function(){var l=0,b;for(b in k)if(k.hasOwnProperty(b)){var e=k[b],f=e.get();l++;e.s=(f-e.b)/(e.dur/e.spd);1<=e.s&&(delete k[b],e.s=1,l--,function(b){setTimeout(function(){a("mina.finish."+b.id,b)})}(e));e.update()}l&&y(q)},e=function(a,r,s,x,G,h,J){a={id:w+(A++).toString(36),start:a,end:r,b:s,s:0,dur:x-s,spd:1,get:G,
set:h,easing:J||e.linear,status:z,speed:d,duration:f,stop:n,pause:u,resume:p,update:b};k[a.id]=a;r=0;for(var K in k)if(k.hasOwnProperty(K)&&(r++,2==r))break;1==r&&y(q);return a};e.time=Date.now||function(){return+new Date};e.getById=function(a){return k[a]||null};e.linear=function(a){return a};e.easeout=function(a){return Math.pow(a,1.7)};e.easein=function(a){return Math.pow(a,0.48)};e.easeinout=function(a){if(1==a)return 1;if(0==a)return 0;var b=0.48-a/1.04,e=Math.sqrt(0.1734+b*b);a=e-b;a=Math.pow(Math.abs(a),
1/3)*(0>a?-1:1);b=-e-b;b=Math.pow(Math.abs(b),1/3)*(0>b?-1:1);a=a+b+0.5;return 3*(1-a)*a*a+a*a*a};e.backin=function(a){return 1==a?1:a*a*(2.70158*a-1.70158)};e.backout=function(a){if(0==a)return 0;a-=1;return a*a*(2.70158*a+1.70158)+1};e.elastic=function(a){return a==!!a?a:Math.pow(2,-10*a)*Math.sin(2*(a-0.075)*Math.PI/0.3)+1};e.bounce=function(a){a<1/2.75?a*=7.5625*a:a<2/2.75?(a-=1.5/2.75,a=7.5625*a*a+0.75):a<2.5/2.75?(a-=2.25/2.75,a=7.5625*a*a+0.9375):(a-=2.625/2.75,a=7.5625*a*a+0.984375);return a};
return N.mina=e}("undefined"==typeof k?function(){}:k),C=function(){function a(c,t){if(c){if(c.tagName)return x(c);if(y(c,"array")&&a.set)return a.set.apply(a,c);if(c instanceof e)return c;if(null==t)return c=G.doc.querySelector(c),x(c)}return new s(null==c?"100%":c,null==t?"100%":t)}function v(c,a){if(a){"#text"==c&&(c=G.doc.createTextNode(a.text||""));"string"==typeof c&&(c=v(c));if("string"==typeof a)return"xlink:"==a.substring(0,6)?c.getAttributeNS(m,a.substring(6)):"xml:"==a.substring(0,4)?c.getAttributeNS(la,
a.substring(4)):c.getAttribute(a);for(var da in a)if(a[h](da)){var b=J(a[da]);b?"xlink:"==da.substring(0,6)?c.setAttributeNS(m,da.substring(6),b):"xml:"==da.substring(0,4)?c.setAttributeNS(la,da.substring(4),b):c.setAttribute(da,b):c.removeAttribute(da)}}else c=G.doc.createElementNS(la,c);return c}function y(c,a){a=J.prototype.toLowerCase.call(a);return"finite"==a?isFinite(c):"array"==a&&(c instanceof Array||Array.isArray&&Array.isArray(c))?!0:"null"==a&&null===c||a==typeof c&&null!==c||"object"==
a&&c===Object(c)||$.call(c).slice(8,-1).toLowerCase()==a}function M(c){if("function"==typeof c||Object(c)!==c)return c;var a=new c.constructor,b;for(b in c)c[h](b)&&(a[b]=M(c[b]));return a}function A(c,a,b){function m(){var e=Array.prototype.slice.call(arguments,0),f=e.join("\u2400"),d=m.cache=m.cache||{},l=m.count=m.count||[];if(d[h](f)){a:for(var e=l,l=f,B=0,H=e.length;B<H;B++)if(e[B]===l){e.push(e.splice(B,1)[0]);break a}return b?b(d[f]):d[f]}1E3<=l.length&&delete d[l.shift()];l.push(f);d[f]=c.apply(a,
e);return b?b(d[f]):d[f]}return m}function w(c,a,b,m,e,f){return null==e?(c-=b,a-=m,c||a?(180*I.atan2(-a,-c)/C+540)%360:0):w(c,a,e,f)-w(b,m,e,f)}function z(c){return c%360*C/180}function d(c){var a=[];c=c.replace(/(?:^|\s)(\w+)\(([^)]+)\)/g,function(c,b,m){m=m.split(/\s*,\s*|\s+/);"rotate"==b&&1==m.length&&m.push(0,0);"scale"==b&&(2<m.length?m=m.slice(0,2):2==m.length&&m.push(0,0),1==m.length&&m.push(m[0],0,0));"skewX"==b?a.push(["m",1,0,I.tan(z(m[0])),1,0,0]):"skewY"==b?a.push(["m",1,I.tan(z(m[0])),
0,1,0,0]):a.push([b.charAt(0)].concat(m));return c});return a}function f(c,t){var b=O(c),m=new a.Matrix;if(b)for(var e=0,f=b.length;e<f;e++){var h=b[e],d=h.length,B=J(h[0]).toLowerCase(),H=h[0]!=B,l=H?m.invert():0,E;"t"==B&&2==d?m.translate(h[1],0):"t"==B&&3==d?H?(d=l.x(0,0),B=l.y(0,0),H=l.x(h[1],h[2]),l=l.y(h[1],h[2]),m.translate(H-d,l-B)):m.translate(h[1],h[2]):"r"==B?2==d?(E=E||t,m.rotate(h[1],E.x+E.width/2,E.y+E.height/2)):4==d&&(H?(H=l.x(h[2],h[3]),l=l.y(h[2],h[3]),m.rotate(h[1],H,l)):m.rotate(h[1],
h[2],h[3])):"s"==B?2==d||3==d?(E=E||t,m.scale(h[1],h[d-1],E.x+E.width/2,E.y+E.height/2)):4==d?H?(H=l.x(h[2],h[3]),l=l.y(h[2],h[3]),m.scale(h[1],h[1],H,l)):m.scale(h[1],h[1],h[2],h[3]):5==d&&(H?(H=l.x(h[3],h[4]),l=l.y(h[3],h[4]),m.scale(h[1],h[2],H,l)):m.scale(h[1],h[2],h[3],h[4])):"m"==B&&7==d&&m.add(h[1],h[2],h[3],h[4],h[5],h[6])}return m}function n(c,t){if(null==t){var m=!0;t="linearGradient"==c.type||"radialGradient"==c.type?c.node.getAttribute("gradientTransform"):"pattern"==c.type?c.node.getAttribute("patternTransform"):
c.node.getAttribute("transform");if(!t)return new a.Matrix;t=d(t)}else t=a._.rgTransform.test(t)?J(t).replace(/\.{3}|\u2026/g,c._.transform||aa):d(t),y(t,"array")&&(t=a.path?a.path.toString.call(t):J(t)),c._.transform=t;var b=f(t,c.getBBox(1));if(m)return b;c.matrix=b}function u(c){c=c.node.ownerSVGElement&&x(c.node.ownerSVGElement)||c.node.parentNode&&x(c.node.parentNode)||a.select("svg")||a(0,0);var t=c.select("defs"),t=null==t?!1:t.node;t||(t=r("defs",c.node).node);return t}function p(c){return c.node.ownerSVGElement&&
x(c.node.ownerSVGElement)||a.select("svg")}function b(c,a,m){function b(c){if(null==c)return aa;if(c==+c)return c;v(B,{width:c});try{return B.getBBox().width}catch(a){return 0}}function h(c){if(null==c)return aa;if(c==+c)return c;v(B,{height:c});try{return B.getBBox().height}catch(a){return 0}}function e(b,B){null==a?d[b]=B(c.attr(b)||0):b==a&&(d=B(null==m?c.attr(b)||0:m))}var f=p(c).node,d={},B=f.querySelector(".svg---mgr");B||(B=v("rect"),v(B,{x:-9E9,y:-9E9,width:10,height:10,"class":"svg---mgr",
fill:"none"}),f.appendChild(B));switch(c.type){case "rect":e("rx",b),e("ry",h);case "image":e("width",b),e("height",h);case "text":e("x",b);e("y",h);break;case "circle":e("cx",b);e("cy",h);e("r",b);break;case "ellipse":e("cx",b);e("cy",h);e("rx",b);e("ry",h);break;case "line":e("x1",b);e("x2",b);e("y1",h);e("y2",h);break;case "marker":e("refX",b);e("markerWidth",b);e("refY",h);e("markerHeight",h);break;case "radialGradient":e("fx",b);e("fy",h);break;case "tspan":e("dx",b);e("dy",h);break;default:e(a,
b)}f.removeChild(B);return d}function q(c){y(c,"array")||(c=Array.prototype.slice.call(arguments,0));for(var a=0,b=0,m=this.node;this[a];)delete this[a++];for(a=0;a<c.length;a++)"set"==c[a].type?c[a].forEach(function(c){m.appendChild(c.node)}):m.appendChild(c[a].node);for(var h=m.childNodes,a=0;a<h.length;a++)this[b++]=x(h[a]);return this}function e(c){if(c.snap in E)return E[c.snap];var a=this.id=V(),b;try{b=c.ownerSVGElement}catch(m){}this.node=c;b&&(this.paper=new s(b));this.type=c.tagName;this.anims=
{};this._={transform:[]};c.snap=a;E[a]=this;"g"==this.type&&(this.add=q);if(this.type in{g:1,mask:1,pattern:1})for(var e in s.prototype)s.prototype[h](e)&&(this[e]=s.prototype[e])}function l(c){this.node=c}function r(c,a){var b=v(c);a.appendChild(b);return x(b)}function s(c,a){var b,m,f,d=s.prototype;if(c&&"svg"==c.tagName){if(c.snap in E)return E[c.snap];var l=c.ownerDocument;b=new e(c);m=c.getElementsByTagName("desc")[0];f=c.getElementsByTagName("defs")[0];m||(m=v("desc"),m.appendChild(l.createTextNode("Created with Snap")),
b.node.appendChild(m));f||(f=v("defs"),b.node.appendChild(f));b.defs=f;for(var ca in d)d[h](ca)&&(b[ca]=d[ca]);b.paper=b.root=b}else b=r("svg",G.doc.body),v(b.node,{height:a,version:1.1,width:c,xmlns:la});return b}function x(c){return!c||c instanceof e||c instanceof l?c:c.tagName&&"svg"==c.tagName.toLowerCase()?new s(c):c.tagName&&"object"==c.tagName.toLowerCase()&&"image/svg+xml"==c.type?new s(c.contentDocument.getElementsByTagName("svg")[0]):new e(c)}a.version="0.3.0";a.toString=function(){return"Snap v"+
this.version};a._={};var G={win:N,doc:N.document};a._.glob=G;var h="hasOwnProperty",J=String,K=parseFloat,U=parseInt,I=Math,P=I.max,Q=I.min,Y=I.abs,C=I.PI,aa="",$=Object.prototype.toString,F=/^\s*((#[a-f\d]{6})|(#[a-f\d]{3})|rgba?\(\s*([\d\.]+%?\s*,\s*[\d\.]+%?\s*,\s*[\d\.]+%?(?:\s*,\s*[\d\.]+%?)?)\s*\)|hsba?\(\s*([\d\.]+(?:deg|\xb0|%)?\s*,\s*[\d\.]+%?\s*,\s*[\d\.]+(?:%?\s*,\s*[\d\.]+)?%?)\s*\)|hsla?\(\s*([\d\.]+(?:deg|\xb0|%)?\s*,\s*[\d\.]+%?\s*,\s*[\d\.]+(?:%?\s*,\s*[\d\.]+)?%?)\s*\))\s*$/i;a._.separator=
RegExp("[,\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]+");var S=RegExp("[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*"),X={hs:1,rg:1},W=RegExp("([a-z])[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029,]*((-?\\d*\\.?\\d*(?:e[\\-+]?\\d+)?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*)+)",
"ig"),ma=RegExp("([rstm])[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029,]*((-?\\d*\\.?\\d*(?:e[\\-+]?\\d+)?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*)+)","ig"),Z=RegExp("(-?\\d*\\.?\\d*(?:e[\\-+]?\\d+)?)[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*,?[\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*",
"ig"),na=0,ba="S"+(+new Date).toString(36),V=function(){return ba+(na++).toString(36)},m="http://www.w3.org/1999/xlink",la="http://www.w3.org/2000/svg",E={},ca=a.url=function(c){return"url('#"+c+"')"};a._.$=v;a._.id=V;a.format=function(){var c=/\{([^\}]+)\}/g,a=/(?:(?:^|\.)(.+?)(?=\[|\.|$|\()|\[('|")(.+?)\2\])(\(\))?/g,b=function(c,b,m){var h=m;b.replace(a,function(c,a,b,m,t){a=a||m;h&&(a in h&&(h=h[a]),"function"==typeof h&&t&&(h=h()))});return h=(null==h||h==m?c:h)+""};return function(a,m){return J(a).replace(c,
function(c,a){return b(c,a,m)})}}();a._.clone=M;a._.cacher=A;a.rad=z;a.deg=function(c){return 180*c/C%360};a.angle=w;a.is=y;a.snapTo=function(c,a,b){b=y(b,"finite")?b:10;if(y(c,"array"))for(var m=c.length;m--;){if(Y(c[m]-a)<=b)return c[m]}else{c=+c;m=a%c;if(m<b)return a-m;if(m>c-b)return a-m+c}return a};a.getRGB=A(function(c){if(!c||(c=J(c)).indexOf("-")+1)return{r:-1,g:-1,b:-1,hex:"none",error:1,toString:ka};if("none"==c)return{r:-1,g:-1,b:-1,hex:"none",toString:ka};!X[h](c.toLowerCase().substring(0,
2))&&"#"!=c.charAt()&&(c=T(c));if(!c)return{r:-1,g:-1,b:-1,hex:"none",error:1,toString:ka};var b,m,e,f,d;if(c=c.match(F)){c[2]&&(e=U(c[2].substring(5),16),m=U(c[2].substring(3,5),16),b=U(c[2].substring(1,3),16));c[3]&&(e=U((d=c[3].charAt(3))+d,16),m=U((d=c[3].charAt(2))+d,16),b=U((d=c[3].charAt(1))+d,16));c[4]&&(d=c[4].split(S),b=K(d[0]),"%"==d[0].slice(-1)&&(b*=2.55),m=K(d[1]),"%"==d[1].slice(-1)&&(m*=2.55),e=K(d[2]),"%"==d[2].slice(-1)&&(e*=2.55),"rgba"==c[1].toLowerCase().slice(0,4)&&(f=K(d[3])),
d[3]&&"%"==d[3].slice(-1)&&(f/=100));if(c[5])return d=c[5].split(S),b=K(d[0]),"%"==d[0].slice(-1)&&(b/=100),m=K(d[1]),"%"==d[1].slice(-1)&&(m/=100),e=K(d[2]),"%"==d[2].slice(-1)&&(e/=100),"deg"!=d[0].slice(-3)&&"\u00b0"!=d[0].slice(-1)||(b/=360),"hsba"==c[1].toLowerCase().slice(0,4)&&(f=K(d[3])),d[3]&&"%"==d[3].slice(-1)&&(f/=100),a.hsb2rgb(b,m,e,f);if(c[6])return d=c[6].split(S),b=K(d[0]),"%"==d[0].slice(-1)&&(b/=100),m=K(d[1]),"%"==d[1].slice(-1)&&(m/=100),e=K(d[2]),"%"==d[2].slice(-1)&&(e/=100),
"deg"!=d[0].slice(-3)&&"\u00b0"!=d[0].slice(-1)||(b/=360),"hsla"==c[1].toLowerCase().slice(0,4)&&(f=K(d[3])),d[3]&&"%"==d[3].slice(-1)&&(f/=100),a.hsl2rgb(b,m,e,f);b=Q(I.round(b),255);m=Q(I.round(m),255);e=Q(I.round(e),255);f=Q(P(f,0),1);c={r:b,g:m,b:e,toString:ka};c.hex="#"+(16777216|e|m<<8|b<<16).toString(16).slice(1);c.opacity=y(f,"finite")?f:1;return c}return{r:-1,g:-1,b:-1,hex:"none",error:1,toString:ka}},a);a.hsb=A(function(c,b,m){return a.hsb2rgb(c,b,m).hex});a.hsl=A(function(c,b,m){return a.hsl2rgb(c,
b,m).hex});a.rgb=A(function(c,a,b,m){if(y(m,"finite")){var e=I.round;return"rgba("+[e(c),e(a),e(b),+m.toFixed(2)]+")"}return"#"+(16777216|b|a<<8|c<<16).toString(16).slice(1)});var T=function(c){var a=G.doc.getElementsByTagName("head")[0]||G.doc.getElementsByTagName("svg")[0];T=A(function(c){if("red"==c.toLowerCase())return"rgb(255, 0, 0)";a.style.color="rgb(255, 0, 0)";a.style.color=c;c=G.doc.defaultView.getComputedStyle(a,aa).getPropertyValue("color");return"rgb(255, 0, 0)"==c?null:c});return T(c)},
qa=function(){return"hsb("+[this.h,this.s,this.b]+")"},ra=function(){return"hsl("+[this.h,this.s,this.l]+")"},ka=function(){return 1==this.opacity||null==this.opacity?this.hex:"rgba("+[this.r,this.g,this.b,this.opacity]+")"},D=function(c,b,m){null==b&&y(c,"object")&&"r"in c&&"g"in c&&"b"in c&&(m=c.b,b=c.g,c=c.r);null==b&&y(c,string)&&(m=a.getRGB(c),c=m.r,b=m.g,m=m.b);if(1<c||1<b||1<m)c/=255,b/=255,m/=255;return[c,b,m]},oa=function(c,b,m,e){c=I.round(255*c);b=I.round(255*b);m=I.round(255*m);c={r:c,
g:b,b:m,opacity:y(e,"finite")?e:1,hex:a.rgb(c,b,m),toString:ka};y(e,"finite")&&(c.opacity=e);return c};a.color=function(c){var b;y(c,"object")&&"h"in c&&"s"in c&&"b"in c?(b=a.hsb2rgb(c),c.r=b.r,c.g=b.g,c.b=b.b,c.opacity=1,c.hex=b.hex):y(c,"object")&&"h"in c&&"s"in c&&"l"in c?(b=a.hsl2rgb(c),c.r=b.r,c.g=b.g,c.b=b.b,c.opacity=1,c.hex=b.hex):(y(c,"string")&&(c=a.getRGB(c)),y(c,"object")&&"r"in c&&"g"in c&&"b"in c&&!("error"in c)?(b=a.rgb2hsl(c),c.h=b.h,c.s=b.s,c.l=b.l,b=a.rgb2hsb(c),c.v=b.b):(c={hex:"none"},
c.r=c.g=c.b=c.h=c.s=c.v=c.l=-1,c.error=1));c.toString=ka;return c};a.hsb2rgb=function(c,a,b,m){y(c,"object")&&"h"in c&&"s"in c&&"b"in c&&(b=c.b,a=c.s,c=c.h,m=c.o);var e,h,d;c=360*c%360/60;d=b*a;a=d*(1-Y(c%2-1));b=e=h=b-d;c=~~c;b+=[d,a,0,0,a,d][c];e+=[a,d,d,a,0,0][c];h+=[0,0,a,d,d,a][c];return oa(b,e,h,m)};a.hsl2rgb=function(c,a,b,m){y(c,"object")&&"h"in c&&"s"in c&&"l"in c&&(b=c.l,a=c.s,c=c.h);if(1<c||1<a||1<b)c/=360,a/=100,b/=100;var e,h,d;c=360*c%360/60;d=2*a*(0.5>b?b:1-b);a=d*(1-Y(c%2-1));b=e=
h=b-d/2;c=~~c;b+=[d,a,0,0,a,d][c];e+=[a,d,d,a,0,0][c];h+=[0,0,a,d,d,a][c];return oa(b,e,h,m)};a.rgb2hsb=function(c,a,b){b=D(c,a,b);c=b[0];a=b[1];b=b[2];var m,e;m=P(c,a,b);e=m-Q(c,a,b);c=((0==e?0:m==c?(a-b)/e:m==a?(b-c)/e+2:(c-a)/e+4)+360)%6*60/360;return{h:c,s:0==e?0:e/m,b:m,toString:qa}};a.rgb2hsl=function(c,a,b){b=D(c,a,b);c=b[0];a=b[1];b=b[2];var m,e,h;m=P(c,a,b);e=Q(c,a,b);h=m-e;c=((0==h?0:m==c?(a-b)/h:m==a?(b-c)/h+2:(c-a)/h+4)+360)%6*60/360;m=(m+e)/2;return{h:c,s:0==h?0:0.5>m?h/(2*m):h/(2-2*
m),l:m,toString:ra}};a.parsePathString=function(c){if(!c)return null;var b=a.path(c);if(b.arr)return a.path.clone(b.arr);var m={a:7,c:6,o:2,h:1,l:2,m:2,r:4,q:4,s:4,t:2,v:1,u:3,z:0},e=[];y(c,"array")&&y(c[0],"array")&&(e=a.path.clone(c));e.length||J(c).replace(W,function(c,a,b){var h=[];c=a.toLowerCase();b.replace(Z,function(c,a){a&&h.push(+a)});"m"==c&&2<h.length&&(e.push([a].concat(h.splice(0,2))),c="l",a="m"==a?"l":"L");"o"==c&&1==h.length&&e.push([a,h[0] ]);if("r"==c)e.push([a].concat(h));else for(;h.length>=
m[c]&&(e.push([a].concat(h.splice(0,m[c]))),m[c]););});e.toString=a.path.toString;b.arr=a.path.clone(e);return e};var O=a.parseTransformString=function(c){if(!c)return null;var b=[];y(c,"array")&&y(c[0],"array")&&(b=a.path.clone(c));b.length||J(c).replace(ma,function(c,a,m){var e=[];a.toLowerCase();m.replace(Z,function(c,a){a&&e.push(+a)});b.push([a].concat(e))});b.toString=a.path.toString;return b};a._.svgTransform2string=d;a._.rgTransform=RegExp("^[a-z][\t\n\x0B\f\r \u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u202f\u205f\u3000\u2028\u2029]*-?\\.?\\d",
"i");a._.transform2matrix=f;a._unit2px=b;a._.getSomeDefs=u;a._.getSomeSVG=p;a.select=function(c){return x(G.doc.querySelector(c))};a.selectAll=function(c){c=G.doc.querySelectorAll(c);for(var b=(a.set||Array)(),m=0;m<c.length;m++)b.push(x(c[m]));return b};setInterval(function(){for(var c in E)if(E[h](c)){var a=E[c],b=a.node;("svg"!=a.type&&!b.ownerSVGElement||"svg"==a.type&&(!b.parentNode||"ownerSVGElement"in b.parentNode&&!b.ownerSVGElement))&&delete E[c]}},1E4);(function(c){function m(c){function a(c,
b){var m=v(c.node,b);(m=(m=m&&m.match(d))&&m[2])&&"#"==m.charAt()&&(m=m.substring(1))&&(f[m]=(f[m]||[]).concat(function(a){var m={};m[b]=ca(a);v(c.node,m)}))}function b(c){var a=v(c.node,"xlink:href");a&&"#"==a.charAt()&&(a=a.substring(1))&&(f[a]=(f[a]||[]).concat(function(a){c.attr("xlink:href","#"+a)}))}var e=c.selectAll("*"),h,d=/^\s*url\(("|'|)(.*)\1\)\s*$/;c=[];for(var f={},l=0,E=e.length;l<E;l++){h=e[l];a(h,"fill");a(h,"stroke");a(h,"filter");a(h,"mask");a(h,"clip-path");b(h);var t=v(h.node,
"id");t&&(v(h.node,{id:h.id}),c.push({old:t,id:h.id}))}l=0;for(E=c.length;l<E;l++)if(e=f[c[l].old])for(h=0,t=e.length;h<t;h++)e[h](c[l].id)}function e(c,a,b){return function(m){m=m.slice(c,a);1==m.length&&(m=m[0]);return b?b(m):m}}function d(c){return function(){var a=c?"<"+this.type:"",b=this.node.attributes,m=this.node.childNodes;if(c)for(var e=0,h=b.length;e<h;e++)a+=" "+b[e].name+'="'+b[e].value.replace(/"/g,'\\"')+'"';if(m.length){c&&(a+=">");e=0;for(h=m.length;e<h;e++)3==m[e].nodeType?a+=m[e].nodeValue:
1==m[e].nodeType&&(a+=x(m[e]).toString());c&&(a+="</"+this.type+">")}else c&&(a+="/>");return a}}c.attr=function(c,a){if(!c)return this;if(y(c,"string"))if(1<arguments.length){var b={};b[c]=a;c=b}else return k("snap.util.getattr."+c,this).firstDefined();for(var m in c)c[h](m)&&k("snap.util.attr."+m,this,c[m]);return this};c.getBBox=function(c){if(!a.Matrix||!a.path)return this.node.getBBox();var b=this,m=new a.Matrix;if(b.removed)return a._.box();for(;"use"==b.type;)if(c||(m=m.add(b.transform().localMatrix.translate(b.attr("x")||
0,b.attr("y")||0))),b.original)b=b.original;else var e=b.attr("xlink:href"),b=b.original=b.node.ownerDocument.getElementById(e.substring(e.indexOf("#")+1));var e=b._,h=a.path.get[b.type]||a.path.get.deflt;try{if(c)return e.bboxwt=h?a.path.getBBox(b.realPath=h(b)):a._.box(b.node.getBBox()),a._.box(e.bboxwt);b.realPath=h(b);b.matrix=b.transform().localMatrix;e.bbox=a.path.getBBox(a.path.map(b.realPath,m.add(b.matrix)));return a._.box(e.bbox)}catch(d){return a._.box()}};var f=function(){return this.string};
c.transform=function(c){var b=this._;if(null==c){var m=this;c=new a.Matrix(this.node.getCTM());for(var e=n(this),h=[e],d=new a.Matrix,l=e.toTransformString(),b=J(e)==J(this.matrix)?J(b.transform):l;"svg"!=m.type&&(m=m.parent());)h.push(n(m));for(m=h.length;m--;)d.add(h[m]);return{string:b,globalMatrix:c,totalMatrix:d,localMatrix:e,diffMatrix:c.clone().add(e.invert()),global:c.toTransformString(),total:d.toTransformString(),local:l,toString:f}}c instanceof a.Matrix?this.matrix=c:n(this,c);this.node&&
("linearGradient"==this.type||"radialGradient"==this.type?v(this.node,{gradientTransform:this.matrix}):"pattern"==this.type?v(this.node,{patternTransform:this.matrix}):v(this.node,{transform:this.matrix}));return this};c.parent=function(){return x(this.node.parentNode)};c.append=c.add=function(c){if(c){if("set"==c.type){var a=this;c.forEach(function(c){a.add(c)});return this}c=x(c);this.node.appendChild(c.node);c.paper=this.paper}return this};c.appendTo=function(c){c&&(c=x(c),c.append(this));return this};
c.prepend=function(c){if(c){if("set"==c.type){var a=this,b;c.forEach(function(c){b?b.after(c):a.prepend(c);b=c});return this}c=x(c);var m=c.parent();this.node.insertBefore(c.node,this.node.firstChild);this.add&&this.add();c.paper=this.paper;this.parent()&&this.parent().add();m&&m.add()}return this};c.prependTo=function(c){c=x(c);c.prepend(this);return this};c.before=function(c){if("set"==c.type){var a=this;c.forEach(function(c){var b=c.parent();a.node.parentNode.insertBefore(c.node,a.node);b&&b.add()});
this.parent().add();return this}c=x(c);var b=c.parent();this.node.parentNode.insertBefore(c.node,this.node);this.parent()&&this.parent().add();b&&b.add();c.paper=this.paper;return this};c.after=function(c){c=x(c);var a=c.parent();this.node.nextSibling?this.node.parentNode.insertBefore(c.node,this.node.nextSibling):this.node.parentNode.appendChild(c.node);this.parent()&&this.parent().add();a&&a.add();c.paper=this.paper;return this};c.insertBefore=function(c){c=x(c);var a=this.parent();c.node.parentNode.insertBefore(this.node,
c.node);this.paper=c.paper;a&&a.add();c.parent()&&c.parent().add();return this};c.insertAfter=function(c){c=x(c);var a=this.parent();c.node.parentNode.insertBefore(this.node,c.node.nextSibling);this.paper=c.paper;a&&a.add();c.parent()&&c.parent().add();return this};c.remove=function(){var c=this.parent();this.node.parentNode&&this.node.parentNode.removeChild(this.node);delete this.paper;this.removed=!0;c&&c.add();return this};c.select=function(c){return x(this.node.querySelector(c))};c.selectAll=
function(c){c=this.node.querySelectorAll(c);for(var b=(a.set||Array)(),m=0;m<c.length;m++)b.push(x(c[m]));return b};c.asPX=function(c,a){null==a&&(a=this.attr(c));return+b(this,c,a)};c.use=function(){var c,a=this.node.id;a||(a=this.id,v(this.node,{id:a}));c="linearGradient"==this.type||"radialGradient"==this.type||"pattern"==this.type?r(this.type,this.node.parentNode):r("use",this.node.parentNode);v(c.node,{"xlink:href":"#"+a});c.original=this;return c};var l=/\S+/g;c.addClass=function(c){var a=(c||
"").match(l)||[];c=this.node;var b=c.className.baseVal,m=b.match(l)||[],e,h,d;if(a.length){for(e=0;d=a[e++];)h=m.indexOf(d),~h||m.push(d);a=m.join(" ");b!=a&&(c.className.baseVal=a)}return this};c.removeClass=function(c){var a=(c||"").match(l)||[];c=this.node;var b=c.className.baseVal,m=b.match(l)||[],e,h;if(m.length){for(e=0;h=a[e++];)h=m.indexOf(h),~h&&m.splice(h,1);a=m.join(" ");b!=a&&(c.className.baseVal=a)}return this};c.hasClass=function(c){return!!~(this.node.className.baseVal.match(l)||[]).indexOf(c)};
c.toggleClass=function(c,a){if(null!=a)return a?this.addClass(c):this.removeClass(c);var b=(c||"").match(l)||[],m=this.node,e=m.className.baseVal,h=e.match(l)||[],d,f,E;for(d=0;E=b[d++];)f=h.indexOf(E),~f?h.splice(f,1):h.push(E);b=h.join(" ");e!=b&&(m.className.baseVal=b);return this};c.clone=function(){var c=x(this.node.cloneNode(!0));v(c.node,"id")&&v(c.node,{id:c.id});m(c);c.insertAfter(this);return c};c.toDefs=function(){u(this).appendChild(this.node);return this};c.pattern=c.toPattern=function(c,
a,b,m){var e=r("pattern",u(this));null==c&&(c=this.getBBox());y(c,"object")&&"x"in c&&(a=c.y,b=c.width,m=c.height,c=c.x);v(e.node,{x:c,y:a,width:b,height:m,patternUnits:"userSpaceOnUse",id:e.id,viewBox:[c,a,b,m].join(" ")});e.node.appendChild(this.node);return e};c.marker=function(c,a,b,m,e,h){var d=r("marker",u(this));null==c&&(c=this.getBBox());y(c,"object")&&"x"in c&&(a=c.y,b=c.width,m=c.height,e=c.refX||c.cx,h=c.refY||c.cy,c=c.x);v(d.node,{viewBox:[c,a,b,m].join(" "),markerWidth:b,markerHeight:m,
orient:"auto",refX:e||0,refY:h||0,id:d.id});d.node.appendChild(this.node);return d};var E=function(c,a,b,m){"function"!=typeof b||b.length||(m=b,b=L.linear);this.attr=c;this.dur=a;b&&(this.easing=b);m&&(this.callback=m)};a._.Animation=E;a.animation=function(c,a,b,m){return new E(c,a,b,m)};c.inAnim=function(){var c=[],a;for(a in this.anims)this.anims[h](a)&&function(a){c.push({anim:new E(a._attrs,a.dur,a.easing,a._callback),mina:a,curStatus:a.status(),status:function(c){return a.status(c)},stop:function(){a.stop()}})}(this.anims[a]);
return c};a.animate=function(c,a,b,m,e,h){"function"!=typeof e||e.length||(h=e,e=L.linear);var d=L.time();c=L(c,a,d,d+m,L.time,b,e);h&&k.once("mina.finish."+c.id,h);return c};c.stop=function(){for(var c=this.inAnim(),a=0,b=c.length;a<b;a++)c[a].stop();return this};c.animate=function(c,a,b,m){"function"!=typeof b||b.length||(m=b,b=L.linear);c instanceof E&&(m=c.callback,b=c.easing,a=b.dur,c=c.attr);var d=[],f=[],l={},t,ca,n,T=this,q;for(q in c)if(c[h](q)){T.equal?(n=T.equal(q,J(c[q])),t=n.from,ca=
n.to,n=n.f):(t=+T.attr(q),ca=+c[q]);var la=y(t,"array")?t.length:1;l[q]=e(d.length,d.length+la,n);d=d.concat(t);f=f.concat(ca)}t=L.time();var p=L(d,f,t,t+a,L.time,function(c){var a={},b;for(b in l)l[h](b)&&(a[b]=l[b](c));T.attr(a)},b);T.anims[p.id]=p;p._attrs=c;p._callback=m;k("snap.animcreated."+T.id,p);k.once("mina.finish."+p.id,function(){delete T.anims[p.id];m&&m.call(T)});k.once("mina.stop."+p.id,function(){delete T.anims[p.id]});return T};var T={};c.data=function(c,b){var m=T[this.id]=T[this.id]||
{};if(0==arguments.length)return k("snap.data.get."+this.id,this,m,null),m;if(1==arguments.length){if(a.is(c,"object")){for(var e in c)c[h](e)&&this.data(e,c[e]);return this}k("snap.data.get."+this.id,this,m[c],c);return m[c]}m[c]=b;k("snap.data.set."+this.id,this,b,c);return this};c.removeData=function(c){null==c?T[this.id]={}:T[this.id]&&delete T[this.id][c];return this};c.outerSVG=c.toString=d(1);c.innerSVG=d()})(e.prototype);a.parse=function(c){var a=G.doc.createDocumentFragment(),b=!0,m=G.doc.createElement("div");
c=J(c);c.match(/^\s*<\s*svg(?:\s|>)/)||(c="<svg>"+c+"</svg>",b=!1);m.innerHTML=c;if(c=m.getElementsByTagName("svg")[0])if(b)a=c;else for(;c.firstChild;)a.appendChild(c.firstChild);m.innerHTML=aa;return new l(a)};l.prototype.select=e.prototype.select;l.prototype.selectAll=e.prototype.selectAll;a.fragment=function(){for(var c=Array.prototype.slice.call(arguments,0),b=G.doc.createDocumentFragment(),m=0,e=c.length;m<e;m++){var h=c[m];h.node&&h.node.nodeType&&b.appendChild(h.node);h.nodeType&&b.appendChild(h);
"string"==typeof h&&b.appendChild(a.parse(h).node)}return new l(b)};a._.make=r;a._.wrap=x;s.prototype.el=function(c,a){var b=r(c,this.node);a&&b.attr(a);return b};k.on("snap.util.getattr",function(){var c=k.nt(),c=c.substring(c.lastIndexOf(".")+1),a=c.replace(/[A-Z]/g,function(c){return"-"+c.toLowerCase()});return pa[h](a)?this.node.ownerDocument.defaultView.getComputedStyle(this.node,null).getPropertyValue(a):v(this.node,c)});var pa={"alignment-baseline":0,"baseline-shift":0,clip:0,"clip-path":0,
"clip-rule":0,color:0,"color-interpolation":0,"color-interpolation-filters":0,"color-profile":0,"color-rendering":0,cursor:0,direction:0,display:0,"dominant-baseline":0,"enable-background":0,fill:0,"fill-opacity":0,"fill-rule":0,filter:0,"flood-color":0,"flood-opacity":0,font:0,"font-family":0,"font-size":0,"font-size-adjust":0,"font-stretch":0,"font-style":0,"font-variant":0,"font-weight":0,"glyph-orientation-horizontal":0,"glyph-orientation-vertical":0,"image-rendering":0,kerning:0,"letter-spacing":0,
"lighting-color":0,marker:0,"marker-end":0,"marker-mid":0,"marker-start":0,mask:0,opacity:0,overflow:0,"pointer-events":0,"shape-rendering":0,"stop-color":0,"stop-opacity":0,stroke:0,"stroke-dasharray":0,"stroke-dashoffset":0,"stroke-linecap":0,"stroke-linejoin":0,"stroke-miterlimit":0,"stroke-opacity":0,"stroke-width":0,"text-anchor":0,"text-decoration":0,"text-rendering":0,"unicode-bidi":0,visibility:0,"word-spacing":0,"writing-mode":0};k.on("snap.util.attr",function(c){var a=k.nt(),b={},a=a.substring(a.lastIndexOf(".")+
1);b[a]=c;var m=a.replace(/-(\w)/gi,function(c,a){return a.toUpperCase()}),a=a.replace(/[A-Z]/g,function(c){return"-"+c.toLowerCase()});pa[h](a)?this.node.style[m]=null==c?aa:c:v(this.node,b)});a.ajax=function(c,a,b,m){var e=new XMLHttpRequest,h=V();if(e){if(y(a,"function"))m=b,b=a,a=null;else if(y(a,"object")){var d=[],f;for(f in a)a.hasOwnProperty(f)&&d.push(encodeURIComponent(f)+"="+encodeURIComponent(a[f]));a=d.join("&")}e.open(a?"POST":"GET",c,!0);a&&(e.setRequestHeader("X-Requested-With","XMLHttpRequest"),
e.setRequestHeader("Content-type","application/x-www-form-urlencoded"));b&&(k.once("snap.ajax."+h+".0",b),k.once("snap.ajax."+h+".200",b),k.once("snap.ajax."+h+".304",b));e.onreadystatechange=function(){4==e.readyState&&k("snap.ajax."+h+"."+e.status,m,e)};if(4==e.readyState)return e;e.send(a);return e}};a.load=function(c,b,m){a.ajax(c,function(c){c=a.parse(c.responseText);m?b.call(m,c):b(c)})};a.getElementByPoint=function(c,a){var b,m,e=G.doc.elementFromPoint(c,a);if(G.win.opera&&"svg"==e.tagName){b=
e;m=b.getBoundingClientRect();b=b.ownerDocument;var h=b.body,d=b.documentElement;b=m.top+(g.win.pageYOffset||d.scrollTop||h.scrollTop)-(d.clientTop||h.clientTop||0);m=m.left+(g.win.pageXOffset||d.scrollLeft||h.scrollLeft)-(d.clientLeft||h.clientLeft||0);h=e.createSVGRect();h.x=c-m;h.y=a-b;h.width=h.height=1;b=e.getIntersectionList(h,null);b.length&&(e=b[b.length-1])}return e?x(e):null};a.plugin=function(c){c(a,e,s,G,l)};return G.win.Snap=a}();C.plugin(function(a,k,y,M,A){function w(a,d,f,b,q,e){null==
d&&"[object SVGMatrix]"==z.call(a)?(this.a=a.a,this.b=a.b,this.c=a.c,this.d=a.d,this.e=a.e,this.f=a.f):null!=a?(this.a=+a,this.b=+d,this.c=+f,this.d=+b,this.e=+q,this.f=+e):(this.a=1,this.c=this.b=0,this.d=1,this.f=this.e=0)}var z=Object.prototype.toString,d=String,f=Math;(function(n){function k(a){return a[0]*a[0]+a[1]*a[1]}function p(a){var d=f.sqrt(k(a));a[0]&&(a[0]/=d);a[1]&&(a[1]/=d)}n.add=function(a,d,e,f,n,p){var k=[[],[],[] ],u=[[this.a,this.c,this.e],[this.b,this.d,this.f],[0,0,1] ];d=[[a,
e,n],[d,f,p],[0,0,1] ];a&&a instanceof w&&(d=[[a.a,a.c,a.e],[a.b,a.d,a.f],[0,0,1] ]);for(a=0;3>a;a++)for(e=0;3>e;e++){for(f=n=0;3>f;f++)n+=u[a][f]*d[f][e];k[a][e]=n}this.a=k[0][0];this.b=k[1][0];this.c=k[0][1];this.d=k[1][1];this.e=k[0][2];this.f=k[1][2];return this};n.invert=function(){var a=this.a*this.d-this.b*this.c;return new w(this.d/a,-this.b/a,-this.c/a,this.a/a,(this.c*this.f-this.d*this.e)/a,(this.b*this.e-this.a*this.f)/a)};n.clone=function(){return new w(this.a,this.b,this.c,this.d,this.e,
this.f)};n.translate=function(a,d){return this.add(1,0,0,1,a,d)};n.scale=function(a,d,e,f){null==d&&(d=a);(e||f)&&this.add(1,0,0,1,e,f);this.add(a,0,0,d,0,0);(e||f)&&this.add(1,0,0,1,-e,-f);return this};n.rotate=function(b,d,e){b=a.rad(b);d=d||0;e=e||0;var l=+f.cos(b).toFixed(9);b=+f.sin(b).toFixed(9);this.add(l,b,-b,l,d,e);return this.add(1,0,0,1,-d,-e)};n.x=function(a,d){return a*this.a+d*this.c+this.e};n.y=function(a,d){return a*this.b+d*this.d+this.f};n.get=function(a){return+this[d.fromCharCode(97+
a)].toFixed(4)};n.toString=function(){return"matrix("+[this.get(0),this.get(1),this.get(2),this.get(3),this.get(4),this.get(5)].join()+")"};n.offset=function(){return[this.e.toFixed(4),this.f.toFixed(4)]};n.determinant=function(){return this.a*this.d-this.b*this.c};n.split=function(){var b={};b.dx=this.e;b.dy=this.f;var d=[[this.a,this.c],[this.b,this.d] ];b.scalex=f.sqrt(k(d[0]));p(d[0]);b.shear=d[0][0]*d[1][0]+d[0][1]*d[1][1];d[1]=[d[1][0]-d[0][0]*b.shear,d[1][1]-d[0][1]*b.shear];b.scaley=f.sqrt(k(d[1]));
p(d[1]);b.shear/=b.scaley;0>this.determinant()&&(b.scalex=-b.scalex);var e=-d[0][1],d=d[1][1];0>d?(b.rotate=a.deg(f.acos(d)),0>e&&(b.rotate=360-b.rotate)):b.rotate=a.deg(f.asin(e));b.isSimple=!+b.shear.toFixed(9)&&(b.scalex.toFixed(9)==b.scaley.toFixed(9)||!b.rotate);b.isSuperSimple=!+b.shear.toFixed(9)&&b.scalex.toFixed(9)==b.scaley.toFixed(9)&&!b.rotate;b.noRotation=!+b.shear.toFixed(9)&&!b.rotate;return b};n.toTransformString=function(a){a=a||this.split();if(+a.shear.toFixed(9))return"m"+[this.get(0),
this.get(1),this.get(2),this.get(3),this.get(4),this.get(5)];a.scalex=+a.scalex.toFixed(4);a.scaley=+a.scaley.toFixed(4);a.rotate=+a.rotate.toFixed(4);return(a.dx||a.dy?"t"+[+a.dx.toFixed(4),+a.dy.toFixed(4)]:"")+(1!=a.scalex||1!=a.scaley?"s"+[a.scalex,a.scaley,0,0]:"")+(a.rotate?"r"+[+a.rotate.toFixed(4),0,0]:"")}})(w.prototype);a.Matrix=w;a.matrix=function(a,d,f,b,k,e){return new w(a,d,f,b,k,e)}});C.plugin(function(a,v,y,M,A){function w(h){return function(d){k.stop();d instanceof A&&1==d.node.childNodes.length&&
("radialGradient"==d.node.firstChild.tagName||"linearGradient"==d.node.firstChild.tagName||"pattern"==d.node.firstChild.tagName)&&(d=d.node.firstChild,b(this).appendChild(d),d=u(d));if(d instanceof v)if("radialGradient"==d.type||"linearGradient"==d.type||"pattern"==d.type){d.node.id||e(d.node,{id:d.id});var f=l(d.node.id)}else f=d.attr(h);else f=a.color(d),f.error?(f=a(b(this).ownerSVGElement).gradient(d))?(f.node.id||e(f.node,{id:f.id}),f=l(f.node.id)):f=d:f=r(f);d={};d[h]=f;e(this.node,d);this.node.style[h]=
x}}function z(a){k.stop();a==+a&&(a+="px");this.node.style.fontSize=a}function d(a){var b=[];a=a.childNodes;for(var e=0,f=a.length;e<f;e++){var l=a[e];3==l.nodeType&&b.push(l.nodeValue);"tspan"==l.tagName&&(1==l.childNodes.length&&3==l.firstChild.nodeType?b.push(l.firstChild.nodeValue):b.push(d(l)))}return b}function f(){k.stop();return this.node.style.fontSize}var n=a._.make,u=a._.wrap,p=a.is,b=a._.getSomeDefs,q=/^url\(#?([^)]+)\)$/,e=a._.$,l=a.url,r=String,s=a._.separator,x="";k.on("snap.util.attr.mask",
function(a){if(a instanceof v||a instanceof A){k.stop();a instanceof A&&1==a.node.childNodes.length&&(a=a.node.firstChild,b(this).appendChild(a),a=u(a));if("mask"==a.type)var d=a;else d=n("mask",b(this)),d.node.appendChild(a.node);!d.node.id&&e(d.node,{id:d.id});e(this.node,{mask:l(d.id)})}});(function(a){k.on("snap.util.attr.clip",a);k.on("snap.util.attr.clip-path",a);k.on("snap.util.attr.clipPath",a)})(function(a){if(a instanceof v||a instanceof A){k.stop();if("clipPath"==a.type)var d=a;else d=
n("clipPath",b(this)),d.node.appendChild(a.node),!d.node.id&&e(d.node,{id:d.id});e(this.node,{"clip-path":l(d.id)})}});k.on("snap.util.attr.fill",w("fill"));k.on("snap.util.attr.stroke",w("stroke"));var G=/^([lr])(?:\(([^)]*)\))?(.*)$/i;k.on("snap.util.grad.parse",function(a){a=r(a);var b=a.match(G);if(!b)return null;a=b[1];var e=b[2],b=b[3],e=e.split(/\s*,\s*/).map(function(a){return+a==a?+a:a});1==e.length&&0==e[0]&&(e=[]);b=b.split("-");b=b.map(function(a){a=a.split(":");var b={color:a[0]};a[1]&&
(b.offset=parseFloat(a[1]));return b});return{type:a,params:e,stops:b}});k.on("snap.util.attr.d",function(b){k.stop();p(b,"array")&&p(b[0],"array")&&(b=a.path.toString.call(b));b=r(b);b.match(/[ruo]/i)&&(b=a.path.toAbsolute(b));e(this.node,{d:b})})(-1);k.on("snap.util.attr.#text",function(a){k.stop();a=r(a);for(a=M.doc.createTextNode(a);this.node.firstChild;)this.node.removeChild(this.node.firstChild);this.node.appendChild(a)})(-1);k.on("snap.util.attr.path",function(a){k.stop();this.attr({d:a})})(-1);
k.on("snap.util.attr.class",function(a){k.stop();this.node.className.baseVal=a})(-1);k.on("snap.util.attr.viewBox",function(a){a=p(a,"object")&&"x"in a?[a.x,a.y,a.width,a.height].join(" "):p(a,"array")?a.join(" "):a;e(this.node,{viewBox:a});k.stop()})(-1);k.on("snap.util.attr.transform",function(a){this.transform(a);k.stop()})(-1);k.on("snap.util.attr.r",function(a){"rect"==this.type&&(k.stop(),e(this.node,{rx:a,ry:a}))})(-1);k.on("snap.util.attr.textpath",function(a){k.stop();if("text"==this.type){var d,
f;if(!a&&this.textPath){for(a=this.textPath;a.node.firstChild;)this.node.appendChild(a.node.firstChild);a.remove();delete this.textPath}else if(p(a,"string")?(d=b(this),a=u(d.parentNode).path(a),d.appendChild(a.node),d=a.id,a.attr({id:d})):(a=u(a),a instanceof v&&(d=a.attr("id"),d||(d=a.id,a.attr({id:d})))),d)if(a=this.textPath,f=this.node,a)a.attr({"xlink:href":"#"+d});else{for(a=e("textPath",{"xlink:href":"#"+d});f.firstChild;)a.appendChild(f.firstChild);f.appendChild(a);this.textPath=u(a)}}})(-1);
k.on("snap.util.attr.text",function(a){if("text"==this.type){for(var b=this.node,d=function(a){var b=e("tspan");if(p(a,"array"))for(var f=0;f<a.length;f++)b.appendChild(d(a[f]));else b.appendChild(M.doc.createTextNode(a));b.normalize&&b.normalize();return b};b.firstChild;)b.removeChild(b.firstChild);for(a=d(a);a.firstChild;)b.appendChild(a.firstChild)}k.stop()})(-1);k.on("snap.util.attr.fontSize",z)(-1);k.on("snap.util.attr.font-size",z)(-1);k.on("snap.util.getattr.transform",function(){k.stop();
return this.transform()})(-1);k.on("snap.util.getattr.textpath",function(){k.stop();return this.textPath})(-1);(function(){function b(d){return function(){k.stop();var b=M.doc.defaultView.getComputedStyle(this.node,null).getPropertyValue("marker-"+d);return"none"==b?b:a(M.doc.getElementById(b.match(q)[1]))}}function d(a){return function(b){k.stop();var d="marker"+a.charAt(0).toUpperCase()+a.substring(1);if(""==b||!b)this.node.style[d]="none";else if("marker"==b.type){var f=b.node.id;f||e(b.node,{id:b.id});
this.node.style[d]=l(f)}}}k.on("snap.util.getattr.marker-end",b("end"))(-1);k.on("snap.util.getattr.markerEnd",b("end"))(-1);k.on("snap.util.getattr.marker-start",b("start"))(-1);k.on("snap.util.getattr.markerStart",b("start"))(-1);k.on("snap.util.getattr.marker-mid",b("mid"))(-1);k.on("snap.util.getattr.markerMid",b("mid"))(-1);k.on("snap.util.attr.marker-end",d("end"))(-1);k.on("snap.util.attr.markerEnd",d("end"))(-1);k.on("snap.util.attr.marker-start",d("start"))(-1);k.on("snap.util.attr.markerStart",
d("start"))(-1);k.on("snap.util.attr.marker-mid",d("mid"))(-1);k.on("snap.util.attr.markerMid",d("mid"))(-1)})();k.on("snap.util.getattr.r",function(){if("rect"==this.type&&e(this.node,"rx")==e(this.node,"ry"))return k.stop(),e(this.node,"rx")})(-1);k.on("snap.util.getattr.text",function(){if("text"==this.type||"tspan"==this.type){k.stop();var a=d(this.node);return 1==a.length?a[0]:a}})(-1);k.on("snap.util.getattr.#text",function(){return this.node.textContent})(-1);k.on("snap.util.getattr.viewBox",
function(){k.stop();var b=e(this.node,"viewBox");if(b)return b=b.split(s),a._.box(+b[0],+b[1],+b[2],+b[3])})(-1);k.on("snap.util.getattr.points",function(){var a=e(this.node,"points");k.stop();if(a)return a.split(s)})(-1);k.on("snap.util.getattr.path",function(){var a=e(this.node,"d");k.stop();return a})(-1);k.on("snap.util.getattr.class",function(){return this.node.className.baseVal})(-1);k.on("snap.util.getattr.fontSize",f)(-1);k.on("snap.util.getattr.font-size",f)(-1)});C.plugin(function(a,v,y,
M,A){function w(a){return a}function z(a){return function(b){return+b.toFixed(3)+a}}var d={"+":function(a,b){return a+b},"-":function(a,b){return a-b},"/":function(a,b){return a/b},"*":function(a,b){return a*b}},f=String,n=/[a-z]+$/i,u=/^\s*([+\-\/*])\s*=\s*([\d.eE+\-]+)\s*([^\d\s]+)?\s*$/;k.on("snap.util.attr",function(a){if(a=f(a).match(u)){var b=k.nt(),b=b.substring(b.lastIndexOf(".")+1),q=this.attr(b),e={};k.stop();var l=a[3]||"",r=q.match(n),s=d[a[1] ];r&&r==l?a=s(parseFloat(q),+a[2]):(q=this.asPX(b),
a=s(this.asPX(b),this.asPX(b,a[2]+l)));isNaN(q)||isNaN(a)||(e[b]=a,this.attr(e))}})(-10);k.on("snap.util.equal",function(a,b){var q=f(this.attr(a)||""),e=f(b).match(u);if(e){k.stop();var l=e[3]||"",r=q.match(n),s=d[e[1] ];if(r&&r==l)return{from:parseFloat(q),to:s(parseFloat(q),+e[2]),f:z(r)};q=this.asPX(a);return{from:q,to:s(q,this.asPX(a,e[2]+l)),f:w}}})(-10)});C.plugin(function(a,v,y,M,A){var w=y.prototype,z=a.is;w.rect=function(a,d,k,p,b,q){var e;null==q&&(q=b);z(a,"object")&&"[object Object]"==
a?e=a:null!=a&&(e={x:a,y:d,width:k,height:p},null!=b&&(e.rx=b,e.ry=q));return this.el("rect",e)};w.circle=function(a,d,k){var p;z(a,"object")&&"[object Object]"==a?p=a:null!=a&&(p={cx:a,cy:d,r:k});return this.el("circle",p)};var d=function(){function a(){this.parentNode.removeChild(this)}return function(d,k){var p=M.doc.createElement("img"),b=M.doc.body;p.style.cssText="position:absolute;left:-9999em;top:-9999em";p.onload=function(){k.call(p);p.onload=p.onerror=null;b.removeChild(p)};p.onerror=a;
b.appendChild(p);p.src=d}}();w.image=function(f,n,k,p,b){var q=this.el("image");if(z(f,"object")&&"src"in f)q.attr(f);else if(null!=f){var e={"xlink:href":f,preserveAspectRatio:"none"};null!=n&&null!=k&&(e.x=n,e.y=k);null!=p&&null!=b?(e.width=p,e.height=b):d(f,function(){a._.$(q.node,{width:this.offsetWidth,height:this.offsetHeight})});a._.$(q.node,e)}return q};w.ellipse=function(a,d,k,p){var b;z(a,"object")&&"[object Object]"==a?b=a:null!=a&&(b={cx:a,cy:d,rx:k,ry:p});return this.el("ellipse",b)};
w.path=function(a){var d;z(a,"object")&&!z(a,"array")?d=a:a&&(d={d:a});return this.el("path",d)};w.group=w.g=function(a){var d=this.el("g");1==arguments.length&&a&&!a.type?d.attr(a):arguments.length&&d.add(Array.prototype.slice.call(arguments,0));return d};w.svg=function(a,d,k,p,b,q,e,l){var r={};z(a,"object")&&null==d?r=a:(null!=a&&(r.x=a),null!=d&&(r.y=d),null!=k&&(r.width=k),null!=p&&(r.height=p),null!=b&&null!=q&&null!=e&&null!=l&&(r.viewBox=[b,q,e,l]));return this.el("svg",r)};w.mask=function(a){var d=
this.el("mask");1==arguments.length&&a&&!a.type?d.attr(a):arguments.length&&d.add(Array.prototype.slice.call(arguments,0));return d};w.ptrn=function(a,d,k,p,b,q,e,l){if(z(a,"object"))var r=a;else arguments.length?(r={},null!=a&&(r.x=a),null!=d&&(r.y=d),null!=k&&(r.width=k),null!=p&&(r.height=p),null!=b&&null!=q&&null!=e&&null!=l&&(r.viewBox=[b,q,e,l])):r={patternUnits:"userSpaceOnUse"};return this.el("pattern",r)};w.use=function(a){return null!=a?(make("use",this.node),a instanceof v&&(a.attr("id")||
a.attr({id:ID()}),a=a.attr("id")),this.el("use",{"xlink:href":a})):v.prototype.use.call(this)};w.text=function(a,d,k){var p={};z(a,"object")?p=a:null!=a&&(p={x:a,y:d,text:k||""});return this.el("text",p)};w.line=function(a,d,k,p){var b={};z(a,"object")?b=a:null!=a&&(b={x1:a,x2:k,y1:d,y2:p});return this.el("line",b)};w.polyline=function(a){1<arguments.length&&(a=Array.prototype.slice.call(arguments,0));var d={};z(a,"object")&&!z(a,"array")?d=a:null!=a&&(d={points:a});return this.el("polyline",d)};
w.polygon=function(a){1<arguments.length&&(a=Array.prototype.slice.call(arguments,0));var d={};z(a,"object")&&!z(a,"array")?d=a:null!=a&&(d={points:a});return this.el("polygon",d)};(function(){function d(){return this.selectAll("stop")}function n(b,d){var f=e("stop"),k={offset:+d+"%"};b=a.color(b);k["stop-color"]=b.hex;1>b.opacity&&(k["stop-opacity"]=b.opacity);e(f,k);this.node.appendChild(f);return this}function u(){if("linearGradient"==this.type){var b=e(this.node,"x1")||0,d=e(this.node,"x2")||
1,f=e(this.node,"y1")||0,k=e(this.node,"y2")||0;return a._.box(b,f,math.abs(d-b),math.abs(k-f))}b=this.node.r||0;return a._.box((this.node.cx||0.5)-b,(this.node.cy||0.5)-b,2*b,2*b)}function p(a,d){function f(a,b){for(var d=(b-u)/(a-w),e=w;e<a;e++)h[e].offset=+(+u+d*(e-w)).toFixed(2);w=a;u=b}var n=k("snap.util.grad.parse",null,d).firstDefined(),p;if(!n)return null;n.params.unshift(a);p="l"==n.type.toLowerCase()?b.apply(0,n.params):q.apply(0,n.params);n.type!=n.type.toLowerCase()&&e(p.node,{gradientUnits:"userSpaceOnUse"});
var h=n.stops,n=h.length,u=0,w=0;n--;for(var v=0;v<n;v++)"offset"in h[v]&&f(v,h[v].offset);h[n].offset=h[n].offset||100;f(n,h[n].offset);for(v=0;v<=n;v++){var y=h[v];p.addStop(y.color,y.offset)}return p}function b(b,k,p,q,w){b=a._.make("linearGradient",b);b.stops=d;b.addStop=n;b.getBBox=u;null!=k&&e(b.node,{x1:k,y1:p,x2:q,y2:w});return b}function q(b,k,p,q,w,h){b=a._.make("radialGradient",b);b.stops=d;b.addStop=n;b.getBBox=u;null!=k&&e(b.node,{cx:k,cy:p,r:q});null!=w&&null!=h&&e(b.node,{fx:w,fy:h});
return b}var e=a._.$;w.gradient=function(a){return p(this.defs,a)};w.gradientLinear=function(a,d,e,f){return b(this.defs,a,d,e,f)};w.gradientRadial=function(a,b,d,e,f){return q(this.defs,a,b,d,e,f)};w.toString=function(){var b=this.node.ownerDocument,d=b.createDocumentFragment(),b=b.createElement("div"),e=this.node.cloneNode(!0);d.appendChild(b);b.appendChild(e);a._.$(e,{xmlns:"http://www.w3.org/2000/svg"});b=b.innerHTML;d.removeChild(d.firstChild);return b};w.clear=function(){for(var a=this.node.firstChild,
b;a;)b=a.nextSibling,"defs"!=a.tagName?a.parentNode.removeChild(a):w.clear.call({node:a}),a=b}})()});C.plugin(function(a,k,y,M){function A(a){var b=A.ps=A.ps||{};b[a]?b[a].sleep=100:b[a]={sleep:100};setTimeout(function(){for(var d in b)b[L](d)&&d!=a&&(b[d].sleep--,!b[d].sleep&&delete b[d])});return b[a]}function w(a,b,d,e){null==a&&(a=b=d=e=0);null==b&&(b=a.y,d=a.width,e=a.height,a=a.x);return{x:a,y:b,width:d,w:d,height:e,h:e,x2:a+d,y2:b+e,cx:a+d/2,cy:b+e/2,r1:F.min(d,e)/2,r2:F.max(d,e)/2,r0:F.sqrt(d*
d+e*e)/2,path:s(a,b,d,e),vb:[a,b,d,e].join(" ")}}function z(){return this.join(",").replace(N,"$1")}function d(a){a=C(a);a.toString=z;return a}function f(a,b,d,h,f,k,l,n,p){if(null==p)return e(a,b,d,h,f,k,l,n);if(0>p||e(a,b,d,h,f,k,l,n)<p)p=void 0;else{var q=0.5,O=1-q,s;for(s=e(a,b,d,h,f,k,l,n,O);0.01<Z(s-p);)q/=2,O+=(s<p?1:-1)*q,s=e(a,b,d,h,f,k,l,n,O);p=O}return u(a,b,d,h,f,k,l,n,p)}function n(b,d){function e(a){return+(+a).toFixed(3)}return a._.cacher(function(a,h,l){a instanceof k&&(a=a.attr("d"));
a=I(a);for(var n,p,D,q,O="",s={},c=0,t=0,r=a.length;t<r;t++){D=a[t];if("M"==D[0])n=+D[1],p=+D[2];else{q=f(n,p,D[1],D[2],D[3],D[4],D[5],D[6]);if(c+q>h){if(d&&!s.start){n=f(n,p,D[1],D[2],D[3],D[4],D[5],D[6],h-c);O+=["C"+e(n.start.x),e(n.start.y),e(n.m.x),e(n.m.y),e(n.x),e(n.y)];if(l)return O;s.start=O;O=["M"+e(n.x),e(n.y)+"C"+e(n.n.x),e(n.n.y),e(n.end.x),e(n.end.y),e(D[5]),e(D[6])].join();c+=q;n=+D[5];p=+D[6];continue}if(!b&&!d)return n=f(n,p,D[1],D[2],D[3],D[4],D[5],D[6],h-c)}c+=q;n=+D[5];p=+D[6]}O+=
D.shift()+D}s.end=O;return n=b?c:d?s:u(n,p,D[0],D[1],D[2],D[3],D[4],D[5],1)},null,a._.clone)}function u(a,b,d,e,h,f,k,l,n){var p=1-n,q=ma(p,3),s=ma(p,2),c=n*n,t=c*n,r=q*a+3*s*n*d+3*p*n*n*h+t*k,q=q*b+3*s*n*e+3*p*n*n*f+t*l,s=a+2*n*(d-a)+c*(h-2*d+a),t=b+2*n*(e-b)+c*(f-2*e+b),x=d+2*n*(h-d)+c*(k-2*h+d),c=e+2*n*(f-e)+c*(l-2*f+e);a=p*a+n*d;b=p*b+n*e;h=p*h+n*k;f=p*f+n*l;l=90-180*F.atan2(s-x,t-c)/S;return{x:r,y:q,m:{x:s,y:t},n:{x:x,y:c},start:{x:a,y:b},end:{x:h,y:f},alpha:l}}function p(b,d,e,h,f,n,k,l){a.is(b,
"array")||(b=[b,d,e,h,f,n,k,l]);b=U.apply(null,b);return w(b.min.x,b.min.y,b.max.x-b.min.x,b.max.y-b.min.y)}function b(a,b,d){return b>=a.x&&b<=a.x+a.width&&d>=a.y&&d<=a.y+a.height}function q(a,d){a=w(a);d=w(d);return b(d,a.x,a.y)||b(d,a.x2,a.y)||b(d,a.x,a.y2)||b(d,a.x2,a.y2)||b(a,d.x,d.y)||b(a,d.x2,d.y)||b(a,d.x,d.y2)||b(a,d.x2,d.y2)||(a.x<d.x2&&a.x>d.x||d.x<a.x2&&d.x>a.x)&&(a.y<d.y2&&a.y>d.y||d.y<a.y2&&d.y>a.y)}function e(a,b,d,e,h,f,n,k,l){null==l&&(l=1);l=(1<l?1:0>l?0:l)/2;for(var p=[-0.1252,
0.1252,-0.3678,0.3678,-0.5873,0.5873,-0.7699,0.7699,-0.9041,0.9041,-0.9816,0.9816],q=[0.2491,0.2491,0.2335,0.2335,0.2032,0.2032,0.1601,0.1601,0.1069,0.1069,0.0472,0.0472],s=0,c=0;12>c;c++)var t=l*p[c]+l,r=t*(t*(-3*a+9*d-9*h+3*n)+6*a-12*d+6*h)-3*a+3*d,t=t*(t*(-3*b+9*e-9*f+3*k)+6*b-12*e+6*f)-3*b+3*e,s=s+q[c]*F.sqrt(r*r+t*t);return l*s}function l(a,b,d){a=I(a);b=I(b);for(var h,f,l,n,k,s,r,O,x,c,t=d?0:[],w=0,v=a.length;w<v;w++)if(x=a[w],"M"==x[0])h=k=x[1],f=s=x[2];else{"C"==x[0]?(x=[h,f].concat(x.slice(1)),
h=x[6],f=x[7]):(x=[h,f,h,f,k,s,k,s],h=k,f=s);for(var G=0,y=b.length;G<y;G++)if(c=b[G],"M"==c[0])l=r=c[1],n=O=c[2];else{"C"==c[0]?(c=[l,n].concat(c.slice(1)),l=c[6],n=c[7]):(c=[l,n,l,n,r,O,r,O],l=r,n=O);var z;var K=x,B=c;z=d;var H=p(K),J=p(B);if(q(H,J)){for(var H=e.apply(0,K),J=e.apply(0,B),H=~~(H/8),J=~~(J/8),U=[],A=[],F={},M=z?0:[],P=0;P<H+1;P++){var C=u.apply(0,K.concat(P/H));U.push({x:C.x,y:C.y,t:P/H})}for(P=0;P<J+1;P++)C=u.apply(0,B.concat(P/J)),A.push({x:C.x,y:C.y,t:P/J});for(P=0;P<H;P++)for(K=
0;K<J;K++){var Q=U[P],L=U[P+1],B=A[K],C=A[K+1],N=0.001>Z(L.x-Q.x)?"y":"x",S=0.001>Z(C.x-B.x)?"y":"x",R;R=Q.x;var Y=Q.y,V=L.x,ea=L.y,fa=B.x,ga=B.y,ha=C.x,ia=C.y;if(W(R,V)<X(fa,ha)||X(R,V)>W(fa,ha)||W(Y,ea)<X(ga,ia)||X(Y,ea)>W(ga,ia))R=void 0;else{var $=(R*ea-Y*V)*(fa-ha)-(R-V)*(fa*ia-ga*ha),aa=(R*ea-Y*V)*(ga-ia)-(Y-ea)*(fa*ia-ga*ha),ja=(R-V)*(ga-ia)-(Y-ea)*(fa-ha);if(ja){var $=$/ja,aa=aa/ja,ja=+$.toFixed(2),ba=+aa.toFixed(2);R=ja<+X(R,V).toFixed(2)||ja>+W(R,V).toFixed(2)||ja<+X(fa,ha).toFixed(2)||
ja>+W(fa,ha).toFixed(2)||ba<+X(Y,ea).toFixed(2)||ba>+W(Y,ea).toFixed(2)||ba<+X(ga,ia).toFixed(2)||ba>+W(ga,ia).toFixed(2)?void 0:{x:$,y:aa}}else R=void 0}R&&F[R.x.toFixed(4)]!=R.y.toFixed(4)&&(F[R.x.toFixed(4)]=R.y.toFixed(4),Q=Q.t+Z((R[N]-Q[N])/(L[N]-Q[N]))*(L.t-Q.t),B=B.t+Z((R[S]-B[S])/(C[S]-B[S]))*(C.t-B.t),0<=Q&&1>=Q&&0<=B&&1>=B&&(z?M++:M.push({x:R.x,y:R.y,t1:Q,t2:B})))}z=M}else z=z?0:[];if(d)t+=z;else{H=0;for(J=z.length;H<J;H++)z[H].segment1=w,z[H].segment2=G,z[H].bez1=x,z[H].bez2=c;t=t.concat(z)}}}return t}
function r(a){var b=A(a);if(b.bbox)return C(b.bbox);if(!a)return w();a=I(a);for(var d=0,e=0,h=[],f=[],l,n=0,k=a.length;n<k;n++)l=a[n],"M"==l[0]?(d=l[1],e=l[2],h.push(d),f.push(e)):(d=U(d,e,l[1],l[2],l[3],l[4],l[5],l[6]),h=h.concat(d.min.x,d.max.x),f=f.concat(d.min.y,d.max.y),d=l[5],e=l[6]);a=X.apply(0,h);l=X.apply(0,f);h=W.apply(0,h);f=W.apply(0,f);f=w(a,l,h-a,f-l);b.bbox=C(f);return f}function s(a,b,d,e,h){if(h)return[["M",+a+ +h,b],["l",d-2*h,0],["a",h,h,0,0,1,h,h],["l",0,e-2*h],["a",h,h,0,0,1,
-h,h],["l",2*h-d,0],["a",h,h,0,0,1,-h,-h],["l",0,2*h-e],["a",h,h,0,0,1,h,-h],["z"] ];a=[["M",a,b],["l",d,0],["l",0,e],["l",-d,0],["z"] ];a.toString=z;return a}function x(a,b,d,e,h){null==h&&null==e&&(e=d);a=+a;b=+b;d=+d;e=+e;if(null!=h){var f=Math.PI/180,l=a+d*Math.cos(-e*f);a+=d*Math.cos(-h*f);var n=b+d*Math.sin(-e*f);b+=d*Math.sin(-h*f);d=[["M",l,n],["A",d,d,0,+(180<h-e),0,a,b] ]}else d=[["M",a,b],["m",0,-e],["a",d,e,0,1,1,0,2*e],["a",d,e,0,1,1,0,-2*e],["z"] ];d.toString=z;return d}function G(b){var e=
A(b);if(e.abs)return d(e.abs);Q(b,"array")&&Q(b&&b[0],"array")||(b=a.parsePathString(b));if(!b||!b.length)return[["M",0,0] ];var h=[],f=0,l=0,n=0,k=0,p=0;"M"==b[0][0]&&(f=+b[0][1],l=+b[0][2],n=f,k=l,p++,h[0]=["M",f,l]);for(var q=3==b.length&&"M"==b[0][0]&&"R"==b[1][0].toUpperCase()&&"Z"==b[2][0].toUpperCase(),s,r,w=p,c=b.length;w<c;w++){h.push(s=[]);r=b[w];p=r[0];if(p!=p.toUpperCase())switch(s[0]=p.toUpperCase(),s[0]){case "A":s[1]=r[1];s[2]=r[2];s[3]=r[3];s[4]=r[4];s[5]=r[5];s[6]=+r[6]+f;s[7]=+r[7]+
l;break;case "V":s[1]=+r[1]+l;break;case "H":s[1]=+r[1]+f;break;case "R":for(var t=[f,l].concat(r.slice(1)),u=2,v=t.length;u<v;u++)t[u]=+t[u]+f,t[++u]=+t[u]+l;h.pop();h=h.concat(P(t,q));break;case "O":h.pop();t=x(f,l,r[1],r[2]);t.push(t[0]);h=h.concat(t);break;case "U":h.pop();h=h.concat(x(f,l,r[1],r[2],r[3]));s=["U"].concat(h[h.length-1].slice(-2));break;case "M":n=+r[1]+f,k=+r[2]+l;default:for(u=1,v=r.length;u<v;u++)s[u]=+r[u]+(u%2?f:l)}else if("R"==p)t=[f,l].concat(r.slice(1)),h.pop(),h=h.concat(P(t,
q)),s=["R"].concat(r.slice(-2));else if("O"==p)h.pop(),t=x(f,l,r[1],r[2]),t.push(t[0]),h=h.concat(t);else if("U"==p)h.pop(),h=h.concat(x(f,l,r[1],r[2],r[3])),s=["U"].concat(h[h.length-1].slice(-2));else for(t=0,u=r.length;t<u;t++)s[t]=r[t];p=p.toUpperCase();if("O"!=p)switch(s[0]){case "Z":f=+n;l=+k;break;case "H":f=s[1];break;case "V":l=s[1];break;case "M":n=s[s.length-2],k=s[s.length-1];default:f=s[s.length-2],l=s[s.length-1]}}h.toString=z;e.abs=d(h);return h}function h(a,b,d,e){return[a,b,d,e,d,
e]}function J(a,b,d,e,h,f){var l=1/3,n=2/3;return[l*a+n*d,l*b+n*e,l*h+n*d,l*f+n*e,h,f]}function K(b,d,e,h,f,l,n,k,p,s){var r=120*S/180,q=S/180*(+f||0),c=[],t,x=a._.cacher(function(a,b,c){var d=a*F.cos(c)-b*F.sin(c);a=a*F.sin(c)+b*F.cos(c);return{x:d,y:a}});if(s)v=s[0],t=s[1],l=s[2],u=s[3];else{t=x(b,d,-q);b=t.x;d=t.y;t=x(k,p,-q);k=t.x;p=t.y;F.cos(S/180*f);F.sin(S/180*f);t=(b-k)/2;v=(d-p)/2;u=t*t/(e*e)+v*v/(h*h);1<u&&(u=F.sqrt(u),e*=u,h*=u);var u=e*e,w=h*h,u=(l==n?-1:1)*F.sqrt(Z((u*w-u*v*v-w*t*t)/
(u*v*v+w*t*t)));l=u*e*v/h+(b+k)/2;var u=u*-h*t/e+(d+p)/2,v=F.asin(((d-u)/h).toFixed(9));t=F.asin(((p-u)/h).toFixed(9));v=b<l?S-v:v;t=k<l?S-t:t;0>v&&(v=2*S+v);0>t&&(t=2*S+t);n&&v>t&&(v-=2*S);!n&&t>v&&(t-=2*S)}if(Z(t-v)>r){var c=t,w=k,G=p;t=v+r*(n&&t>v?1:-1);k=l+e*F.cos(t);p=u+h*F.sin(t);c=K(k,p,e,h,f,0,n,w,G,[t,c,l,u])}l=t-v;f=F.cos(v);r=F.sin(v);n=F.cos(t);t=F.sin(t);l=F.tan(l/4);e=4/3*e*l;l*=4/3*h;h=[b,d];b=[b+e*r,d-l*f];d=[k+e*t,p-l*n];k=[k,p];b[0]=2*h[0]-b[0];b[1]=2*h[1]-b[1];if(s)return[b,d,k].concat(c);
c=[b,d,k].concat(c).join().split(",");s=[];k=0;for(p=c.length;k<p;k++)s[k]=k%2?x(c[k-1],c[k],q).y:x(c[k],c[k+1],q).x;return s}function U(a,b,d,e,h,f,l,k){for(var n=[],p=[[],[] ],s,r,c,t,q=0;2>q;++q)0==q?(r=6*a-12*d+6*h,s=-3*a+9*d-9*h+3*l,c=3*d-3*a):(r=6*b-12*e+6*f,s=-3*b+9*e-9*f+3*k,c=3*e-3*b),1E-12>Z(s)?1E-12>Z(r)||(s=-c/r,0<s&&1>s&&n.push(s)):(t=r*r-4*c*s,c=F.sqrt(t),0>t||(t=(-r+c)/(2*s),0<t&&1>t&&n.push(t),s=(-r-c)/(2*s),0<s&&1>s&&n.push(s)));for(r=q=n.length;q--;)s=n[q],c=1-s,p[0][q]=c*c*c*a+3*
c*c*s*d+3*c*s*s*h+s*s*s*l,p[1][q]=c*c*c*b+3*c*c*s*e+3*c*s*s*f+s*s*s*k;p[0][r]=a;p[1][r]=b;p[0][r+1]=l;p[1][r+1]=k;p[0].length=p[1].length=r+2;return{min:{x:X.apply(0,p[0]),y:X.apply(0,p[1])},max:{x:W.apply(0,p[0]),y:W.apply(0,p[1])}}}function I(a,b){var e=!b&&A(a);if(!b&&e.curve)return d(e.curve);var f=G(a),l=b&&G(b),n={x:0,y:0,bx:0,by:0,X:0,Y:0,qx:null,qy:null},k={x:0,y:0,bx:0,by:0,X:0,Y:0,qx:null,qy:null},p=function(a,b,c){if(!a)return["C",b.x,b.y,b.x,b.y,b.x,b.y];a[0]in{T:1,Q:1}||(b.qx=b.qy=null);
switch(a[0]){case "M":b.X=a[1];b.Y=a[2];break;case "A":a=["C"].concat(K.apply(0,[b.x,b.y].concat(a.slice(1))));break;case "S":"C"==c||"S"==c?(c=2*b.x-b.bx,b=2*b.y-b.by):(c=b.x,b=b.y);a=["C",c,b].concat(a.slice(1));break;case "T":"Q"==c||"T"==c?(b.qx=2*b.x-b.qx,b.qy=2*b.y-b.qy):(b.qx=b.x,b.qy=b.y);a=["C"].concat(J(b.x,b.y,b.qx,b.qy,a[1],a[2]));break;case "Q":b.qx=a[1];b.qy=a[2];a=["C"].concat(J(b.x,b.y,a[1],a[2],a[3],a[4]));break;case "L":a=["C"].concat(h(b.x,b.y,a[1],a[2]));break;case "H":a=["C"].concat(h(b.x,
b.y,a[1],b.y));break;case "V":a=["C"].concat(h(b.x,b.y,b.x,a[1]));break;case "Z":a=["C"].concat(h(b.x,b.y,b.X,b.Y))}return a},s=function(a,b){if(7<a[b].length){a[b].shift();for(var c=a[b];c.length;)q[b]="A",l&&(u[b]="A"),a.splice(b++,0,["C"].concat(c.splice(0,6)));a.splice(b,1);v=W(f.length,l&&l.length||0)}},r=function(a,b,c,d,e){a&&b&&"M"==a[e][0]&&"M"!=b[e][0]&&(b.splice(e,0,["M",d.x,d.y]),c.bx=0,c.by=0,c.x=a[e][1],c.y=a[e][2],v=W(f.length,l&&l.length||0))},q=[],u=[],c="",t="",x=0,v=W(f.length,
l&&l.length||0);for(;x<v;x++){f[x]&&(c=f[x][0]);"C"!=c&&(q[x]=c,x&&(t=q[x-1]));f[x]=p(f[x],n,t);"A"!=q[x]&&"C"==c&&(q[x]="C");s(f,x);l&&(l[x]&&(c=l[x][0]),"C"!=c&&(u[x]=c,x&&(t=u[x-1])),l[x]=p(l[x],k,t),"A"!=u[x]&&"C"==c&&(u[x]="C"),s(l,x));r(f,l,n,k,x);r(l,f,k,n,x);var w=f[x],z=l&&l[x],y=w.length,U=l&&z.length;n.x=w[y-2];n.y=w[y-1];n.bx=$(w[y-4])||n.x;n.by=$(w[y-3])||n.y;k.bx=l&&($(z[U-4])||k.x);k.by=l&&($(z[U-3])||k.y);k.x=l&&z[U-2];k.y=l&&z[U-1]}l||(e.curve=d(f));return l?[f,l]:f}function P(a,
b){for(var d=[],e=0,h=a.length;h-2*!b>e;e+=2){var f=[{x:+a[e-2],y:+a[e-1]},{x:+a[e],y:+a[e+1]},{x:+a[e+2],y:+a[e+3]},{x:+a[e+4],y:+a[e+5]}];b?e?h-4==e?f[3]={x:+a[0],y:+a[1]}:h-2==e&&(f[2]={x:+a[0],y:+a[1]},f[3]={x:+a[2],y:+a[3]}):f[0]={x:+a[h-2],y:+a[h-1]}:h-4==e?f[3]=f[2]:e||(f[0]={x:+a[e],y:+a[e+1]});d.push(["C",(-f[0].x+6*f[1].x+f[2].x)/6,(-f[0].y+6*f[1].y+f[2].y)/6,(f[1].x+6*f[2].x-f[3].x)/6,(f[1].y+6*f[2].y-f[3].y)/6,f[2].x,f[2].y])}return d}y=k.prototype;var Q=a.is,C=a._.clone,L="hasOwnProperty",
N=/,?([a-z]),?/gi,$=parseFloat,F=Math,S=F.PI,X=F.min,W=F.max,ma=F.pow,Z=F.abs;M=n(1);var na=n(),ba=n(0,1),V=a._unit2px;a.path=A;a.path.getTotalLength=M;a.path.getPointAtLength=na;a.path.getSubpath=function(a,b,d){if(1E-6>this.getTotalLength(a)-d)return ba(a,b).end;a=ba(a,d,1);return b?ba(a,b).end:a};y.getTotalLength=function(){if(this.node.getTotalLength)return this.node.getTotalLength()};y.getPointAtLength=function(a){return na(this.attr("d"),a)};y.getSubpath=function(b,d){return a.path.getSubpath(this.attr("d"),
b,d)};a._.box=w;a.path.findDotsAtSegment=u;a.path.bezierBBox=p;a.path.isPointInsideBBox=b;a.path.isBBoxIntersect=q;a.path.intersection=function(a,b){return l(a,b)};a.path.intersectionNumber=function(a,b){return l(a,b,1)};a.path.isPointInside=function(a,d,e){var h=r(a);return b(h,d,e)&&1==l(a,[["M",d,e],["H",h.x2+10] ],1)%2};a.path.getBBox=r;a.path.get={path:function(a){return a.attr("path")},circle:function(a){a=V(a);return x(a.cx,a.cy,a.r)},ellipse:function(a){a=V(a);return x(a.cx||0,a.cy||0,a.rx,
a.ry)},rect:function(a){a=V(a);return s(a.x||0,a.y||0,a.width,a.height,a.rx,a.ry)},image:function(a){a=V(a);return s(a.x||0,a.y||0,a.width,a.height)},line:function(a){return"M"+[a.attr("x1")||0,a.attr("y1")||0,a.attr("x2"),a.attr("y2")]},polyline:function(a){return"M"+a.attr("points")},polygon:function(a){return"M"+a.attr("points")+"z"},deflt:function(a){a=a.node.getBBox();return s(a.x,a.y,a.width,a.height)}};a.path.toRelative=function(b){var e=A(b),h=String.prototype.toLowerCase;if(e.rel)return d(e.rel);
a.is(b,"array")&&a.is(b&&b[0],"array")||(b=a.parsePathString(b));var f=[],l=0,n=0,k=0,p=0,s=0;"M"==b[0][0]&&(l=b[0][1],n=b[0][2],k=l,p=n,s++,f.push(["M",l,n]));for(var r=b.length;s<r;s++){var q=f[s]=[],x=b[s];if(x[0]!=h.call(x[0]))switch(q[0]=h.call(x[0]),q[0]){case "a":q[1]=x[1];q[2]=x[2];q[3]=x[3];q[4]=x[4];q[5]=x[5];q[6]=+(x[6]-l).toFixed(3);q[7]=+(x[7]-n).toFixed(3);break;case "v":q[1]=+(x[1]-n).toFixed(3);break;case "m":k=x[1],p=x[2];default:for(var c=1,t=x.length;c<t;c++)q[c]=+(x[c]-(c%2?l:
n)).toFixed(3)}else for(f[s]=[],"m"==x[0]&&(k=x[1]+l,p=x[2]+n),q=0,c=x.length;q<c;q++)f[s][q]=x[q];x=f[s].length;switch(f[s][0]){case "z":l=k;n=p;break;case "h":l+=+f[s][x-1];break;case "v":n+=+f[s][x-1];break;default:l+=+f[s][x-2],n+=+f[s][x-1]}}f.toString=z;e.rel=d(f);return f};a.path.toAbsolute=G;a.path.toCubic=I;a.path.map=function(a,b){if(!b)return a;var d,e,h,f,l,n,k;a=I(a);h=0;for(l=a.length;h<l;h++)for(k=a[h],f=1,n=k.length;f<n;f+=2)d=b.x(k[f],k[f+1]),e=b.y(k[f],k[f+1]),k[f]=d,k[f+1]=e;return a};
a.path.toString=z;a.path.clone=d});C.plugin(function(a,v,y,C){var A=Math.max,w=Math.min,z=function(a){this.items=[];this.bindings={};this.length=0;this.type="set";if(a)for(var f=0,n=a.length;f<n;f++)a[f]&&(this[this.items.length]=this.items[this.items.length]=a[f],this.length++)};v=z.prototype;v.push=function(){for(var a,f,n=0,k=arguments.length;n<k;n++)if(a=arguments[n])f=this.items.length,this[f]=this.items[f]=a,this.length++;return this};v.pop=function(){this.length&&delete this[this.length--];
return this.items.pop()};v.forEach=function(a,f){for(var n=0,k=this.items.length;n<k&&!1!==a.call(f,this.items[n],n);n++);return this};v.animate=function(d,f,n,u){"function"!=typeof n||n.length||(u=n,n=L.linear);d instanceof a._.Animation&&(u=d.callback,n=d.easing,f=n.dur,d=d.attr);var p=arguments;if(a.is(d,"array")&&a.is(p[p.length-1],"array"))var b=!0;var q,e=function(){q?this.b=q:q=this.b},l=0,r=u&&function(){l++==this.length&&u.call(this)};return this.forEach(function(a,l){k.once("snap.animcreated."+
a.id,e);b?p[l]&&a.animate.apply(a,p[l]):a.animate(d,f,n,r)})};v.remove=function(){for(;this.length;)this.pop().remove();return this};v.bind=function(a,f,k){var u={};if("function"==typeof f)this.bindings[a]=f;else{var p=k||a;this.bindings[a]=function(a){u[p]=a;f.attr(u)}}return this};v.attr=function(a){var f={},k;for(k in a)if(this.bindings[k])this.bindings[k](a[k]);else f[k]=a[k];a=0;for(k=this.items.length;a<k;a++)this.items[a].attr(f);return this};v.clear=function(){for(;this.length;)this.pop()};
v.splice=function(a,f,k){a=0>a?A(this.length+a,0):a;f=A(0,w(this.length-a,f));var u=[],p=[],b=[],q;for(q=2;q<arguments.length;q++)b.push(arguments[q]);for(q=0;q<f;q++)p.push(this[a+q]);for(;q<this.length-a;q++)u.push(this[a+q]);var e=b.length;for(q=0;q<e+u.length;q++)this.items[a+q]=this[a+q]=q<e?b[q]:u[q-e];for(q=this.items.length=this.length-=f-e;this[q];)delete this[q++];return new z(p)};v.exclude=function(a){for(var f=0,k=this.length;f<k;f++)if(this[f]==a)return this.splice(f,1),!0;return!1};
v.insertAfter=function(a){for(var f=this.items.length;f--;)this.items[f].insertAfter(a);return this};v.getBBox=function(){for(var a=[],f=[],k=[],u=[],p=this.items.length;p--;)if(!this.items[p].removed){var b=this.items[p].getBBox();a.push(b.x);f.push(b.y);k.push(b.x+b.width);u.push(b.y+b.height)}a=w.apply(0,a);f=w.apply(0,f);k=A.apply(0,k);u=A.apply(0,u);return{x:a,y:f,x2:k,y2:u,width:k-a,height:u-f,cx:a+(k-a)/2,cy:f+(u-f)/2}};v.clone=function(a){a=new z;for(var f=0,k=this.items.length;f<k;f++)a.push(this.items[f].clone());
return a};v.toString=function(){return"Snap\u2018s set"};v.type="set";a.set=function(){var a=new z;arguments.length&&a.push.apply(a,Array.prototype.slice.call(arguments,0));return a}});C.plugin(function(a,v,y,C){function A(a){var b=a[0];switch(b.toLowerCase()){case "t":return[b,0,0];case "m":return[b,1,0,0,1,0,0];case "r":return 4==a.length?[b,0,a[2],a[3] ]:[b,0];case "s":return 5==a.length?[b,1,1,a[3],a[4] ]:3==a.length?[b,1,1]:[b,1]}}function w(b,d,f){d=q(d).replace(/\.{3}|\u2026/g,b);b=a.parseTransformString(b)||
[];d=a.parseTransformString(d)||[];for(var k=Math.max(b.length,d.length),p=[],v=[],h=0,w,z,y,I;h<k;h++){y=b[h]||A(d[h]);I=d[h]||A(y);if(y[0]!=I[0]||"r"==y[0].toLowerCase()&&(y[2]!=I[2]||y[3]!=I[3])||"s"==y[0].toLowerCase()&&(y[3]!=I[3]||y[4]!=I[4])){b=a._.transform2matrix(b,f());d=a._.transform2matrix(d,f());p=[["m",b.a,b.b,b.c,b.d,b.e,b.f] ];v=[["m",d.a,d.b,d.c,d.d,d.e,d.f] ];break}p[h]=[];v[h]=[];w=0;for(z=Math.max(y.length,I.length);w<z;w++)w in y&&(p[h][w]=y[w]),w in I&&(v[h][w]=I[w])}return{from:u(p),
to:u(v),f:n(p)}}function z(a){return a}function d(a){return function(b){return+b.toFixed(3)+a}}function f(b){return a.rgb(b[0],b[1],b[2])}function n(a){var b=0,d,f,k,n,h,p,q=[];d=0;for(f=a.length;d<f;d++){h="[";p=['"'+a[d][0]+'"'];k=1;for(n=a[d].length;k<n;k++)p[k]="val["+b++ +"]";h+=p+"]";q[d]=h}return Function("val","return Snap.path.toString.call(["+q+"])")}function u(a){for(var b=[],d=0,f=a.length;d<f;d++)for(var k=1,n=a[d].length;k<n;k++)b.push(a[d][k]);return b}var p={},b=/[a-z]+$/i,q=String;
p.stroke=p.fill="colour";v.prototype.equal=function(a,b){return k("snap.util.equal",this,a,b).firstDefined()};k.on("snap.util.equal",function(e,k){var r,s;r=q(this.attr(e)||"");var x=this;if(r==+r&&k==+k)return{from:+r,to:+k,f:z};if("colour"==p[e])return r=a.color(r),s=a.color(k),{from:[r.r,r.g,r.b,r.opacity],to:[s.r,s.g,s.b,s.opacity],f:f};if("transform"==e||"gradientTransform"==e||"patternTransform"==e)return k instanceof a.Matrix&&(k=k.toTransformString()),a._.rgTransform.test(k)||(k=a._.svgTransform2string(k)),
w(r,k,function(){return x.getBBox(1)});if("d"==e||"path"==e)return r=a.path.toCubic(r,k),{from:u(r[0]),to:u(r[1]),f:n(r[0])};if("points"==e)return r=q(r).split(a._.separator),s=q(k).split(a._.separator),{from:r,to:s,f:function(a){return a}};aUnit=r.match(b);s=q(k).match(b);return aUnit&&aUnit==s?{from:parseFloat(r),to:parseFloat(k),f:d(aUnit)}:{from:this.asPX(e),to:this.asPX(e,k),f:z}})});C.plugin(function(a,v,y,C){var A=v.prototype,w="createTouch"in C.doc;v="click dblclick mousedown mousemove mouseout mouseover mouseup touchstart touchmove touchend touchcancel".split(" ");
var z={mousedown:"touchstart",mousemove:"touchmove",mouseup:"touchend"},d=function(a,b){var d="y"==a?"scrollTop":"scrollLeft",e=b&&b.node?b.node.ownerDocument:C.doc;return e[d in e.documentElement?"documentElement":"body"][d]},f=function(){this.returnValue=!1},n=function(){return this.originalEvent.preventDefault()},u=function(){this.cancelBubble=!0},p=function(){return this.originalEvent.stopPropagation()},b=function(){if(C.doc.addEventListener)return function(a,b,e,f){var k=w&&z[b]?z[b]:b,l=function(k){var l=
d("y",f),q=d("x",f);if(w&&z.hasOwnProperty(b))for(var r=0,u=k.targetTouches&&k.targetTouches.length;r<u;r++)if(k.targetTouches[r].target==a||a.contains(k.targetTouches[r].target)){u=k;k=k.targetTouches[r];k.originalEvent=u;k.preventDefault=n;k.stopPropagation=p;break}return e.call(f,k,k.clientX+q,k.clientY+l)};b!==k&&a.addEventListener(b,l,!1);a.addEventListener(k,l,!1);return function(){b!==k&&a.removeEventListener(b,l,!1);a.removeEventListener(k,l,!1);return!0}};if(C.doc.attachEvent)return function(a,
b,e,h){var k=function(a){a=a||h.node.ownerDocument.window.event;var b=d("y",h),k=d("x",h),k=a.clientX+k,b=a.clientY+b;a.preventDefault=a.preventDefault||f;a.stopPropagation=a.stopPropagation||u;return e.call(h,a,k,b)};a.attachEvent("on"+b,k);return function(){a.detachEvent("on"+b,k);return!0}}}(),q=[],e=function(a){for(var b=a.clientX,e=a.clientY,f=d("y"),l=d("x"),n,p=q.length;p--;){n=q[p];if(w)for(var r=a.touches&&a.touches.length,u;r--;){if(u=a.touches[r],u.identifier==n.el._drag.id||n.el.node.contains(u.target)){b=
u.clientX;e=u.clientY;(a.originalEvent?a.originalEvent:a).preventDefault();break}}else a.preventDefault();b+=l;e+=f;k("snap.drag.move."+n.el.id,n.move_scope||n.el,b-n.el._drag.x,e-n.el._drag.y,b,e,a)}},l=function(b){a.unmousemove(e).unmouseup(l);for(var d=q.length,f;d--;)f=q[d],f.el._drag={},k("snap.drag.end."+f.el.id,f.end_scope||f.start_scope||f.move_scope||f.el,b);q=[]};for(y=v.length;y--;)(function(d){a[d]=A[d]=function(e,f){a.is(e,"function")&&(this.events=this.events||[],this.events.push({name:d,
f:e,unbind:b(this.node||document,d,e,f||this)}));return this};a["un"+d]=A["un"+d]=function(a){for(var b=this.events||[],e=b.length;e--;)if(b[e].name==d&&(b[e].f==a||!a)){b[e].unbind();b.splice(e,1);!b.length&&delete this.events;break}return this}})(v[y]);A.hover=function(a,b,d,e){return this.mouseover(a,d).mouseout(b,e||d)};A.unhover=function(a,b){return this.unmouseover(a).unmouseout(b)};var r=[];A.drag=function(b,d,f,h,n,p){function u(r,v,w){(r.originalEvent||r).preventDefault();this._drag.x=v;
this._drag.y=w;this._drag.id=r.identifier;!q.length&&a.mousemove(e).mouseup(l);q.push({el:this,move_scope:h,start_scope:n,end_scope:p});d&&k.on("snap.drag.start."+this.id,d);b&&k.on("snap.drag.move."+this.id,b);f&&k.on("snap.drag.end."+this.id,f);k("snap.drag.start."+this.id,n||h||this,v,w,r)}if(!arguments.length){var v;return this.drag(function(a,b){this.attr({transform:v+(v?"T":"t")+[a,b]})},function(){v=this.transform().local})}this._drag={};r.push({el:this,start:u});this.mousedown(u);return this};
A.undrag=function(){for(var b=r.length;b--;)r[b].el==this&&(this.unmousedown(r[b].start),r.splice(b,1),k.unbind("snap.drag.*."+this.id));!r.length&&a.unmousemove(e).unmouseup(l);return this}});C.plugin(function(a,v,y,C){y=y.prototype;var A=/^\s*url\((.+)\)/,w=String,z=a._.$;a.filter={};y.filter=function(d){var f=this;"svg"!=f.type&&(f=f.paper);d=a.parse(w(d));var k=a._.id(),u=z("filter");z(u,{id:k,filterUnits:"userSpaceOnUse"});u.appendChild(d.node);f.defs.appendChild(u);return new v(u)};k.on("snap.util.getattr.filter",
function(){k.stop();var d=z(this.node,"filter");if(d)return(d=w(d).match(A))&&a.select(d[1])});k.on("snap.util.attr.filter",function(d){if(d instanceof v&&"filter"==d.type){k.stop();var f=d.node.id;f||(z(d.node,{id:d.id}),f=d.id);z(this.node,{filter:a.url(f)})}d&&"none"!=d||(k.stop(),this.node.removeAttribute("filter"))});a.filter.blur=function(d,f){null==d&&(d=2);return a.format('<feGaussianBlur stdDeviation="{def}"/>',{def:null==f?d:[d,f]})};a.filter.blur.toString=function(){return this()};a.filter.shadow=
function(d,f,k,u,p){"string"==typeof k&&(p=u=k,k=4);"string"!=typeof u&&(p=u,u="#000");null==k&&(k=4);null==p&&(p=1);null==d&&(d=0,f=2);null==f&&(f=d);u=a.color(u||"#000");return a.format('<feGaussianBlur in="SourceAlpha" stdDeviation="{blur}"/><feOffset dx="{dx}" dy="{dy}" result="offsetblur"/><feFlood flood-color="{color}"/><feComposite in2="offsetblur" operator="in"/><feComponentTransfer><feFuncA type="linear" slope="{opacity}"/></feComponentTransfer><feMerge><feMergeNode/><feMergeNode in="SourceGraphic"/></feMerge>',
{color:u,dx:d,dy:f,blur:k,opacity:p})};a.filter.shadow.toString=function(){return this()};a.filter.grayscale=function(d){null==d&&(d=1);return a.format('<feColorMatrix type="matrix" values="{a} {b} {c} 0 0 {d} {e} {f} 0 0 {g} {b} {h} 0 0 0 0 0 1 0"/>',{a:0.2126+0.7874*(1-d),b:0.7152-0.7152*(1-d),c:0.0722-0.0722*(1-d),d:0.2126-0.2126*(1-d),e:0.7152+0.2848*(1-d),f:0.0722-0.0722*(1-d),g:0.2126-0.2126*(1-d),h:0.0722+0.9278*(1-d)})};a.filter.grayscale.toString=function(){return this()};a.filter.sepia=
function(d){null==d&&(d=1);return a.format('<feColorMatrix type="matrix" values="{a} {b} {c} 0 0 {d} {e} {f} 0 0 {g} {h} {i} 0 0 0 0 0 1 0"/>',{a:0.393+0.607*(1-d),b:0.769-0.769*(1-d),c:0.189-0.189*(1-d),d:0.349-0.349*(1-d),e:0.686+0.314*(1-d),f:0.168-0.168*(1-d),g:0.272-0.272*(1-d),h:0.534-0.534*(1-d),i:0.131+0.869*(1-d)})};a.filter.sepia.toString=function(){return this()};a.filter.saturate=function(d){null==d&&(d=1);return a.format('<feColorMatrix type="saturate" values="{amount}"/>',{amount:1-
d})};a.filter.saturate.toString=function(){return this()};a.filter.hueRotate=function(d){return a.format('<feColorMatrix type="hueRotate" values="{angle}"/>',{angle:d||0})};a.filter.hueRotate.toString=function(){return this()};a.filter.invert=function(d){null==d&&(d=1);return a.format('<feComponentTransfer><feFuncR type="table" tableValues="{amount} {amount2}"/><feFuncG type="table" tableValues="{amount} {amount2}"/><feFuncB type="table" tableValues="{amount} {amount2}"/></feComponentTransfer>',{amount:d,
amount2:1-d})};a.filter.invert.toString=function(){return this()};a.filter.brightness=function(d){null==d&&(d=1);return a.format('<feComponentTransfer><feFuncR type="linear" slope="{amount}"/><feFuncG type="linear" slope="{amount}"/><feFuncB type="linear" slope="{amount}"/></feComponentTransfer>',{amount:d})};a.filter.brightness.toString=function(){return this()};a.filter.contrast=function(d){null==d&&(d=1);return a.format('<feComponentTransfer><feFuncR type="linear" slope="{amount}" intercept="{amount2}"/><feFuncG type="linear" slope="{amount}" intercept="{amount2}"/><feFuncB type="linear" slope="{amount}" intercept="{amount2}"/></feComponentTransfer>',
{amount:d,amount2:0.5-d/2})};a.filter.contrast.toString=function(){return this()}});return C});

]]> </script>
<script> <![CDATA[

(function (glob, factory) {
    // AMD support
    if (typeof define === "function" && define.amd) {
        // Define as an anonymous module
        define("Gadfly", ["Snap.svg"], function (Snap) {
            return factory(Snap);
        });
    } else {
        // Browser globals (glob is window)
        // Snap adds itself to window
        glob.Gadfly = factory(glob.Snap);
    }
}(this, function (Snap) {

var Gadfly = {};

// Get an x/y coordinate value in pixels
var xPX = function(fig, x) {
    var client_box = fig.node.getBoundingClientRect();
    return x * fig.node.viewBox.baseVal.width / client_box.width;
};

var yPX = function(fig, y) {
    var client_box = fig.node.getBoundingClientRect();
    return y * fig.node.viewBox.baseVal.height / client_box.height;
};


Snap.plugin(function (Snap, Element, Paper, global) {
    // Traverse upwards from a snap element to find and return the first
    // note with the "plotroot" class.
    Element.prototype.plotroot = function () {
        var element = this;
        while (!element.hasClass("plotroot") && element.parent() != null) {
            element = element.parent();
        }
        return element;
    };

    Element.prototype.svgroot = function () {
        var element = this;
        while (element.node.nodeName != "svg" && element.parent() != null) {
            element = element.parent();
        }
        return element;
    };

    Element.prototype.plotbounds = function () {
        var root = this.plotroot()
        var bbox = root.select(".guide.background").node.getBBox();
        return {
            x0: bbox.x,
            x1: bbox.x + bbox.width,
            y0: bbox.y,
            y1: bbox.y + bbox.height
        };
    };

    Element.prototype.plotcenter = function () {
        var root = this.plotroot()
        var bbox = root.select(".guide.background").node.getBBox();
        return {
            x: bbox.x + bbox.width / 2,
            y: bbox.y + bbox.height / 2
        };
    };

    // Emulate IE style mouseenter/mouseleave events, since Microsoft always
    // does everything right.
    // See: http://www.dynamic-tools.net/toolbox/isMouseLeaveOrEnter/
    var events = ["mouseenter", "mouseleave"];

    for (i in events) {
        (function (event_name) {
            var event_name = events[i];
            Element.prototype[event_name] = function (fn, scope) {
                if (Snap.is(fn, "function")) {
                    var fn2 = function (event) {
                        if (event.type != "mouseover" && event.type != "mouseout") {
                            return;
                        }

                        var reltg = event.relatedTarget ? event.relatedTarget :
                            event.type == "mouseout" ? event.toElement : event.fromElement;
                        while (reltg && reltg != this.node) reltg = reltg.parentNode;

                        if (reltg != this.node) {
                            return fn.apply(this, event);
                        }
                    };

                    if (event_name == "mouseenter") {
                        this.mouseover(fn2, scope);
                    } else {
                        this.mouseout(fn2, scope);
                    }
                }
                return this;
            };
        })(events[i]);
    }


    Element.prototype.mousewheel = function (fn, scope) {
        if (Snap.is(fn, "function")) {
            var el = this;
            var fn2 = function (event) {
                fn.apply(el, [event]);
            };
        }

        this.node.addEventListener(
            /Firefox/i.test(navigator.userAgent) ? "DOMMouseScroll" : "mousewheel",
            fn2);

        return this;
    };


    // Snap's attr function can be too slow for things like panning/zooming.
    // This is a function to directly update element attributes without going
    // through eve.
    Element.prototype.attribute = function(key, val) {
        if (val === undefined) {
            return this.node.getAttribute(key, val);
        } else {
            return this.node.setAttribute(key, val);
        }
    };
});


// When the plot is moused over, emphasize the grid lines.
Gadfly.plot_mouseover = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);

    var xgridlines = root.select(".xgridlines"),
        ygridlines = root.select(".ygridlines");

    xgridlines.data("unfocused_strokedash",
                    xgridlines.attr("stroke-dasharray").replace(/px/g, "mm"))
    ygridlines.data("unfocused_strokedash",
                    ygridlines.attr("stroke-dasharray").replace(/px/g, "mm"))

    // emphasize grid lines
    var destcolor = root.data("focused_xgrid_color");
    xgridlines.attr("stroke-dasharray", "none")
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    destcolor = root.data("focused_ygrid_color");
    ygridlines.attr("stroke-dasharray", "none")
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    // reveal zoom slider
    root.select(".zoomslider")
        .animate({opacity: 1.0}, 250);
};


// Unemphasize grid lines on mouse out.
Gadfly.plot_mouseout = function(event) {
    var root = this.plotroot();
    var xgridlines = root.select(".xgridlines"),
        ygridlines = root.select(".ygridlines");

    var destcolor = root.data("unfocused_xgrid_color");

    xgridlines.attr("stroke-dasharray", xgridlines.data("unfocused_strokedash"))
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    destcolor = root.data("unfocused_ygrid_color");
    ygridlines.attr("stroke-dasharray", ygridlines.data("unfocused_strokedash"))
              .selectAll("path")
              .animate({stroke: destcolor}, 250);

    // hide zoom slider
    root.select(".zoomslider")
        .animate({opacity: 0.0}, 250);
};


var set_geometry_transform = function(root, tx, ty, scale) {
    var xscalable = root.hasClass("xscalable"),
        yscalable = root.hasClass("yscalable");

    var old_scale = root.data("scale");

    var xscale = xscalable ? scale : 1.0,
        yscale = yscalable ? scale : 1.0;

    tx = xscalable ? tx : 0.0;
    ty = yscalable ? ty : 0.0;

    var t = new Snap.Matrix().translate(tx, ty).scale(xscale, yscale);

    root.selectAll(".geometry, image")
        .forEach(function (element, i) {
            element.transform(t);
        });

    bounds = root.plotbounds();

    if (yscalable) {
        var xfixed_t = new Snap.Matrix().translate(0, ty).scale(1.0, yscale);
        root.selectAll(".xfixed")
            .forEach(function (element, i) {
                element.transform(xfixed_t);
            });

        root.select(".ylabels")
            .transform(xfixed_t)
            .selectAll("text")
            .forEach(function (element, i) {
                if (element.attribute("gadfly:inscale") == "true") {
                    var cx = element.asPX("x"),
                        cy = element.asPX("y");
                    var st = element.data("static_transform");
                    unscale_t = new Snap.Matrix();
                    unscale_t.scale(1, 1/scale, cx, cy).add(st);
                    element.transform(unscale_t);

                    var y = cy * scale + ty;
                    element.attr("visibility",
                        bounds.y0 <= y && y <= bounds.y1 ? "visible" : "hidden");
                }
            });
    }

    if (xscalable) {
        var yfixed_t = new Snap.Matrix().translate(tx, 0).scale(xscale, 1.0);
        var xtrans = new Snap.Matrix().translate(tx, 0);
        root.selectAll(".yfixed")
            .forEach(function (element, i) {
                element.transform(yfixed_t);
            });

        root.select(".xlabels")
            .transform(yfixed_t)
            .selectAll("text")
            .forEach(function (element, i) {
                if (element.attribute("gadfly:inscale") == "true") {
                    var cx = element.asPX("x"),
                        cy = element.asPX("y");
                    var st = element.data("static_transform");
                    unscale_t = new Snap.Matrix();
                    unscale_t.scale(1/scale, 1, cx, cy).add(st);

                    element.transform(unscale_t);

                    var x = cx * scale + tx;
                    element.attr("visibility",
                        bounds.x0 <= x && x <= bounds.x1 ? "visible" : "hidden");
                    }
            });
    }

    // we must unscale anything that is scale invariance: widths, raiduses, etc.
    var size_attribs = ["font-size"];
    var unscaled_selection = ".geometry, .geometry *";
    if (xscalable) {
        size_attribs.push("rx");
        unscaled_selection += ", .xgridlines";
    }
    if (yscalable) {
        size_attribs.push("ry");
        unscaled_selection += ", .ygridlines";
    }

    root.selectAll(unscaled_selection)
        .forEach(function (element, i) {
            // circle need special help
            if (element.node.nodeName == "circle") {
                var cx = element.attribute("cx"),
                    cy = element.attribute("cy");
                unscale_t = new Snap.Matrix().scale(1/xscale, 1/yscale,
                                                        cx, cy);
                element.transform(unscale_t);
                return;
            }

            for (i in size_attribs) {
                var key = size_attribs[i];
                var val = parseFloat(element.attribute(key));
                if (val !== undefined && val != 0 && !isNaN(val)) {
                    element.attribute(key, val * old_scale / scale);
                }
            }
        });
};


// Find the most appropriate tick scale and update label visibility.
var update_tickscale = function(root, scale, axis) {
    if (!root.hasClass(axis + "scalable")) return;

    var tickscales = root.data(axis + "tickscales");
    var best_tickscale = 1.0;
    var best_tickscale_dist = Infinity;
    for (tickscale in tickscales) {
        var dist = Math.abs(Math.log(tickscale) - Math.log(scale));
        if (dist < best_tickscale_dist) {
            best_tickscale_dist = dist;
            best_tickscale = tickscale;
        }
    }

    if (best_tickscale != root.data(axis + "tickscale")) {
        root.data(axis + "tickscale", best_tickscale);
        var mark_inscale_gridlines = function (element, i) {
            var inscale = element.attr("gadfly:scale") == best_tickscale;
            element.attribute("gadfly:inscale", inscale);
            element.attr("visibility", inscale ? "visible" : "hidden");
        };

        var mark_inscale_labels = function (element, i) {
            var inscale = element.attr("gadfly:scale") == best_tickscale;
            element.attribute("gadfly:inscale", inscale);
            element.attr("visibility", inscale ? "visible" : "hidden");
        };

        root.select("." + axis + "gridlines").selectAll("path").forEach(mark_inscale_gridlines);
        root.select("." + axis + "labels").selectAll("text").forEach(mark_inscale_labels);
    }
};


var set_plot_pan_zoom = function(root, tx, ty, scale) {
    var old_scale = root.data("scale");
    var bounds = root.plotbounds();

    var width = bounds.x1 - bounds.x0,
        height = bounds.y1 - bounds.y0;

    // compute the viewport derived from tx, ty, and scale
    var x_min = -width * scale - (scale * width - width),
        x_max = width * scale,
        y_min = -height * scale - (scale * height - height),
        y_max = height * scale;

    var x0 = bounds.x0 - scale * bounds.x0,
        y0 = bounds.y0 - scale * bounds.y0;

    var tx = Math.max(Math.min(tx - x0, x_max), x_min),
        ty = Math.max(Math.min(ty - y0, y_max), y_min);

    tx += x0;
    ty += y0;

    // when the scale change, we may need to alter which set of
    // ticks is being displayed
    if (scale != old_scale) {
        update_tickscale(root, scale, "x");
        update_tickscale(root, scale, "y");
    }

    set_geometry_transform(root, tx, ty, scale);

    root.data("scale", scale);
    root.data("tx", tx);
    root.data("ty", ty);
};


var scale_centered_translation = function(root, scale) {
    var bounds = root.plotbounds();

    var width = bounds.x1 - bounds.x0,
        height = bounds.y1 - bounds.y0;

    var tx0 = root.data("tx"),
        ty0 = root.data("ty");

    var scale0 = root.data("scale");

    // how off from center the current view is
    var xoff = tx0 - (bounds.x0 * (1 - scale0) + (width * (1 - scale0)) / 2),
        yoff = ty0 - (bounds.y0 * (1 - scale0) + (height * (1 - scale0)) / 2);

    // rescale offsets
    xoff = xoff * scale / scale0;
    yoff = yoff * scale / scale0;

    // adjust for the panel position being scaled
    var x_edge_adjust = bounds.x0 * (1 - scale),
        y_edge_adjust = bounds.y0 * (1 - scale);

    return {
        x: xoff + x_edge_adjust + (width - width * scale) / 2,
        y: yoff + y_edge_adjust + (height - height * scale) / 2
    };
};


// Initialize data for panning zooming if it isn't already.
var init_pan_zoom = function(root) {
    if (root.data("zoompan-ready")) {
        return;
    }

    // The non-scaling-stroke trick. Rather than try to correct for the
    // stroke-width when zooming, we force it to a fixed value.
    var px_per_mm = root.node.getCTM().a;

    // Drag events report deltas in pixels, which we'd like to convert to
    // millimeters.
    root.data("px_per_mm", px_per_mm);

    root.selectAll("path")
        .forEach(function (element, i) {
        sw = element.asPX("stroke-width") * px_per_mm;
        if (sw > 0) {
            element.attribute("stroke-width", sw);
            element.attribute("vector-effect", "non-scaling-stroke");
        }
    });

    // Store ticks labels original tranformation
    root.selectAll(".xlabels > text, .ylabels > text")
        .forEach(function (element, i) {
            var lm = element.transform().localMatrix;
            element.data("static_transform",
                new Snap.Matrix(lm.a, lm.b, lm.c, lm.d, lm.e, lm.f));
        });

    if (root.data("tx") === undefined) root.data("tx", 0);
    if (root.data("ty") === undefined) root.data("ty", 0);
    if (root.data("scale") === undefined) root.data("scale", 1.0);
    if (root.data("xtickscales") === undefined) {

        // index all the tick scales that are listed
        var xtickscales = {};
        var ytickscales = {};
        var add_x_tick_scales = function (element, i) {
            xtickscales[element.attribute("gadfly:scale")] = true;
        };
        var add_y_tick_scales = function (element, i) {
            ytickscales[element.attribute("gadfly:scale")] = true;
        };

        root.select(".xgridlines").selectAll("path").forEach(add_x_tick_scales);
        root.select(".ygridlines").selectAll("path").forEach(add_y_tick_scales);
        root.select(".xlabels").selectAll("text").forEach(add_x_tick_scales);
        root.select(".ylabels").selectAll("text").forEach(add_y_tick_scales);

        root.data("xtickscales", xtickscales);
        root.data("ytickscales", ytickscales);
        root.data("xtickscale", 1.0);
    }

    var min_scale = 1.0, max_scale = 1.0;
    for (scale in xtickscales) {
        min_scale = Math.min(min_scale, scale);
        max_scale = Math.max(max_scale, scale);
    }
    for (scale in ytickscales) {
        min_scale = Math.min(min_scale, scale);
        max_scale = Math.max(max_scale, scale);
    }
    root.data("min_scale", min_scale);
    root.data("max_scale", max_scale);

    // store the original positions of labels
    root.select(".xlabels")
        .selectAll("text")
        .forEach(function (element, i) {
            element.data("x", element.asPX("x"));
        });

    root.select(".ylabels")
        .selectAll("text")
        .forEach(function (element, i) {
            element.data("y", element.asPX("y"));
        });

    // mark grid lines and ticks as in or out of scale.
    var mark_inscale = function (element, i) {
        element.attribute("gadfly:inscale", element.attribute("gadfly:scale") == 1.0);
    };

    root.select(".xgridlines").selectAll("path").forEach(mark_inscale);
    root.select(".ygridlines").selectAll("path").forEach(mark_inscale);
    root.select(".xlabels").selectAll("text").forEach(mark_inscale);
    root.select(".ylabels").selectAll("text").forEach(mark_inscale);

    // figure out the upper ond lower bounds on panning using the maximum
    // and minum grid lines
    var bounds = root.plotbounds();
    var pan_bounds = {
        x0: 0.0,
        y0: 0.0,
        x1: 0.0,
        y1: 0.0
    };

    root.select(".xgridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                var bbox = element.node.getBBox();
                if (bounds.x1 - bbox.x < pan_bounds.x0) {
                    pan_bounds.x0 = bounds.x1 - bbox.x;
                }
                if (bounds.x0 - bbox.x > pan_bounds.x1) {
                    pan_bounds.x1 = bounds.x0 - bbox.x;
                }
            }
        });

    root.select(".ygridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                var bbox = element.node.getBBox();
                if (bounds.y1 - bbox.y < pan_bounds.y0) {
                    pan_bounds.y0 = bounds.y1 - bbox.y;
                }
                if (bounds.y0 - bbox.y > pan_bounds.y1) {
                    pan_bounds.y1 = bounds.y0 - bbox.y;
                }
            }
        });

    // nudge these values a little
    pan_bounds.x0 -= 5;
    pan_bounds.x1 += 5;
    pan_bounds.y0 -= 5;
    pan_bounds.y1 += 5;
    root.data("pan_bounds", pan_bounds);

    // Set all grid lines at scale 1.0 to visible. Out of bounds lines
    // will be clipped.
    root.select(".xgridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                element.attr("visibility", "visible");
            }
        });

    root.select(".ygridlines")
        .selectAll("path")
        .forEach(function (element, i) {
            if (element.attribute("gadfly:inscale") == "true") {
                element.attr("visibility", "visible");
            }
        });

    root.data("zoompan-ready", true)
};


// Panning
Gadfly.guide_background_drag_onmove = function(dx, dy, x, y, event) {
    var root = this.plotroot();
    var px_per_mm = root.data("px_per_mm");
    dx /= px_per_mm;
    dy /= px_per_mm;

    var tx0 = root.data("tx"),
        ty0 = root.data("ty");

    var dx0 = root.data("dx"),
        dy0 = root.data("dy");

    root.data("dx", dx);
    root.data("dy", dy);

    dx = dx - dx0;
    dy = dy - dy0;

    var tx = tx0 + dx,
        ty = ty0 + dy;

    set_plot_pan_zoom(root, tx, ty, root.data("scale"));
};


Gadfly.guide_background_drag_onstart = function(x, y, event) {
    var root = this.plotroot();
    root.data("dx", 0);
    root.data("dy", 0);
    init_pan_zoom(root);
};


Gadfly.guide_background_drag_onend = function(event) {
    var root = this.plotroot();
};


Gadfly.guide_background_scroll = function(event) {
    if (event.shiftKey) {
        var root = this.plotroot();
        init_pan_zoom(root);
        var new_scale = root.data("scale") * Math.pow(2, 0.002 * event.wheelDelta);
        new_scale = Math.max(
            root.data("min_scale"),
            Math.min(root.data("max_scale"), new_scale))
        update_plot_scale(root, new_scale);
        event.stopPropagation();
    }
};


Gadfly.zoomslider_button_mouseover = function(event) {
    this.select(".button_logo")
         .animate({fill: this.data("mouseover_color")}, 100);
};


Gadfly.zoomslider_button_mouseout = function(event) {
     this.select(".button_logo")
         .animate({fill: this.data("mouseout_color")}, 100);
};


Gadfly.zoomslider_zoomout_click = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);
    var min_scale = root.data("min_scale"),
        scale = root.data("scale");
    Snap.animate(
        scale,
        Math.max(min_scale, scale / 1.5),
        function (new_scale) {
            update_plot_scale(root, new_scale);
        },
        200);
};


Gadfly.zoomslider_zoomin_click = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);
    var max_scale = root.data("max_scale"),
        scale = root.data("scale");

    Snap.animate(
        scale,
        Math.min(max_scale, scale * 1.5),
        function (new_scale) {
            update_plot_scale(root, new_scale);
        },
        200);
};


Gadfly.zoomslider_track_click = function(event) {
    // TODO
};


Gadfly.zoomslider_thumb_mousedown = function(event) {
    this.animate({fill: this.data("mouseover_color")}, 100);
};


Gadfly.zoomslider_thumb_mouseup = function(event) {
    this.animate({fill: this.data("mouseout_color")}, 100);
};


// compute the position in [0, 1] of the zoom slider thumb from the current scale
var slider_position_from_scale = function(scale, min_scale, max_scale) {
    if (scale >= 1.0) {
        return 0.5 + 0.5 * (Math.log(scale) / Math.log(max_scale));
    }
    else {
        return 0.5 * (Math.log(scale) - Math.log(min_scale)) / (0 - Math.log(min_scale));
    }
}


var update_plot_scale = function(root, new_scale) {
    var trans = scale_centered_translation(root, new_scale);
    set_plot_pan_zoom(root, trans.x, trans.y, new_scale);

    root.selectAll(".zoomslider_thumb")
        .forEach(function (element, i) {
            var min_pos = element.data("min_pos"),
                max_pos = element.data("max_pos"),
                min_scale = root.data("min_scale"),
                max_scale = root.data("max_scale");
            var xmid = (min_pos + max_pos) / 2;
            var xpos = slider_position_from_scale(new_scale, min_scale, max_scale);
            element.transform(new Snap.Matrix().translate(
                Math.max(min_pos, Math.min(
                         max_pos, min_pos + (max_pos - min_pos) * xpos)) - xmid, 0));
    });
};


Gadfly.zoomslider_thumb_dragmove = function(dx, dy, x, y) {
    var root = this.plotroot();
    var min_pos = this.data("min_pos"),
        max_pos = this.data("max_pos"),
        min_scale = root.data("min_scale"),
        max_scale = root.data("max_scale"),
        old_scale = root.data("old_scale");

    var px_per_mm = root.data("px_per_mm");
    dx /= px_per_mm;
    dy /= px_per_mm;

    var xmid = (min_pos + max_pos) / 2;
    var xpos = slider_position_from_scale(old_scale, min_scale, max_scale) +
                   dx / (max_pos - min_pos);

    // compute the new scale
    var new_scale;
    if (xpos >= 0.5) {
        new_scale = Math.exp(2.0 * (xpos - 0.5) * Math.log(max_scale));
    }
    else {
        new_scale = Math.exp(2.0 * xpos * (0 - Math.log(min_scale)) +
                        Math.log(min_scale));
    }
    new_scale = Math.min(max_scale, Math.max(min_scale, new_scale));

    update_plot_scale(root, new_scale);
};


Gadfly.zoomslider_thumb_dragstart = function(event) {
    var root = this.plotroot();
    init_pan_zoom(root);

    // keep track of what the scale was when we started dragging
    root.data("old_scale", root.data("scale"));
};


Gadfly.zoomslider_thumb_dragend = function(event) {
};


var toggle_color_class = function(root, color_class, ison) {
    var guides = root.selectAll(".guide." + color_class + ",.guide ." + color_class);
    var geoms = root.selectAll(".geometry." + color_class + ",.geometry ." + color_class);
    if (ison) {
        guides.animate({opacity: 0.5}, 250);
        geoms.animate({opacity: 0.0}, 250);
    } else {
        guides.animate({opacity: 1.0}, 250);
        geoms.animate({opacity: 1.0}, 250);
    }
};


Gadfly.colorkey_swatch_click = function(event) {
    var root = this.plotroot();
    var color_class = this.data("color_class");

    if (event.shiftKey) {
        root.selectAll(".colorkey text")
            .forEach(function (element) {
                var other_color_class = element.data("color_class");
                if (other_color_class != color_class) {
                    toggle_color_class(root, other_color_class,
                                       element.attr("opacity") == 1.0);
                }
            });
    } else {
        toggle_color_class(root, color_class, this.attr("opacity") == 1.0);
    }
};


return Gadfly;

}));


//@ sourceURL=gadfly.js

(function (glob, factory) {
    // AMD support
      if (typeof require === "function" && typeof define === "function" && define.amd) {
        require(["Snap.svg", "Gadfly"], function (Snap, Gadfly) {
            factory(Snap, Gadfly);
        });
      } else {
          factory(glob.Snap, glob.Gadfly);
      }
})(window, function (Snap, Gadfly) {
    var fig = Snap("#fig-8226a61cd72e412e8cc8f049f5a87d42");
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-4")
   .drag(function() {}, function() {}, function() {});
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-6")
   .data("color_class", "color_f1")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-7")
   .data("color_class", "color_f2")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-8")
   .data("color_class", "color_f3")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-10")
   .data("color_class", "color_f1")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-11")
   .data("color_class", "color_f2")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-12")
   .data("color_class", "color_f3")
.click(Gadfly.colorkey_swatch_click)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-15")
   .mouseenter(Gadfly.plot_mouseover)
.mouseleave(Gadfly.plot_mouseout)
.mousewheel(Gadfly.guide_background_scroll)
.drag(Gadfly.guide_background_drag_onmove,
      Gadfly.guide_background_drag_onstart,
      Gadfly.guide_background_drag_onend)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-19")
   .plotroot().data("unfocused_ygrid_color", "#D0D0E0")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-19")
   .plotroot().data("focused_ygrid_color", "#A0A0A0")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-149")
   .plotroot().data("unfocused_xgrid_color", "#D0D0E0")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-149")
   .plotroot().data("focused_xgrid_color", "#A0A0A0")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-267")
   .data("mouseover_color", "#cd5c5c")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-267")
   .data("mouseout_color", "#6a6a6a")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-267")
   .click(Gadfly.zoomslider_zoomin_click)
.mouseenter(Gadfly.zoomslider_button_mouseover)
.mouseleave(Gadfly.zoomslider_button_mouseout)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-271")
   .data("max_pos", 97.77)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-271")
   .data("min_pos", 80.77)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-271")
   .click(Gadfly.zoomslider_track_click);
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-273")
   .data("max_pos", 97.77)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-273")
   .data("min_pos", 80.77)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-273")
   .data("mouseover_color", "#cd5c5c")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-273")
   .data("mouseout_color", "#6a6a6a")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-273")
   .drag(Gadfly.zoomslider_thumb_dragmove,
     Gadfly.zoomslider_thumb_dragstart,
     Gadfly.zoomslider_thumb_dragend)
.mousedown(Gadfly.zoomslider_thumb_mousedown)
.mouseup(Gadfly.zoomslider_thumb_mouseup)
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-275")
   .data("mouseover_color", "#cd5c5c")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-275")
   .data("mouseout_color", "#6a6a6a")
;
fig.select("#fig-8226a61cd72e412e8cc8f049f5a87d42-element-275")
   .click(Gadfly.zoomslider_zoomout_click)
.mouseenter(Gadfly.zoomslider_button_mouseover)
.mouseleave(Gadfly.zoomslider_button_mouseout)
;
    });
]]> </script>
</svg>


