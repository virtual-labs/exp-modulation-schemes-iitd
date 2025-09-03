  <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
        <h2>Minimum Shift Keying (MSK)</h2>
        <p>In digital modulation, <strong>minimum-shift keying (MSK)</strong> is a type of continuous-phase frequency-shift keying. Similar to OQPSK, MSK is encoded with bits alternating between quadrature components, with the Q component delayed by half the symbol period.</p>
        <p>However, instead of square pulses as OQPSK uses, MSK encodes each bit as a half sinusoid. This results in a constant-modulus signal, which reduces problems caused by non-linear distortion. In addition to being viewed as related to OQPSK, MSK can also be viewed as a continuous phase frequency shift keyed (CPFSK) signal with a frequency separation of one half the bit rate. This specific frequency separation ensures that the phase shift over a bit period is exactly ±π/2.</p>
        <h3>Mathematical representation:</h3>
        <p>The resulting MSK signal can be represented by the formula:</p>
        <div class="equation">
            $$s(t) = a_I(t) \cos\left(\frac{\pi t}{2T}\right) \cos(\omega_c t) - a_Q(t) \sin\left(\frac{\pi t}{2T}\right) \sin(\omega_c t)$$
        </div>
<p>
  where \( a_I(t) \) and \( a_Q(t) \) encode the even and odd information respectively with a sequence of square pulses of duration \( 2T \), and \( \omega_c \) is the carrier angular frequency. Using the trigonometric identity, this can be rewritten in a form where the phase and frequency modulation are more obvious:
</p>
        <div class="equation">
            $$s(t) = \cos\left(\omega_c t + \phi_k(t)\right)$$
            <p>where the continuously-varying phase \( \phi_k(t) \) is given by:</p>
            $$\phi_k(t) = b(t) \frac{\pi t}{2T} + \phi_0$$
        </div>
<p>
  Here, \( b(t) \) is +1 when \( a_I(t) = a_Q(t) \) and -1 if they are of opposite signs, and \( \phi_0 \) is an initial phase offset which depends on the previous symbols. The phase changes continuously and linearly within each bit period, and the transitions occur at multiples of \( T \).
</p>
        <h3>Reason for Minimum Shift Keying, MSK</h3>
        <p>It is found that binary data consisting of sharp transitions between "one" and "zero" states and vice versa potentially creates signals that have sidebands extending out a long way from the carrier. This wide spectral occupancy creates problems for many radio communications systems, as any sidebands outside the allowed bandwidth cause interference to adjacent channels and any radio communications links that may be using them. MSK's continuous phase property significantly reduces these sidebands compared to abrupt phase-shift keying schemes.</p>
        <h2>Gaussian Minimum Shift Keying (GMSK)</h2>
        <p><strong>Gaussian Minimum Shift Keying (GMSK)</strong> is a variation of MSK that further improves spectral efficiency. Before modulation, the digital data pulses are shaped by a <strong>Gaussian low-pass filter</strong>. This pre-modulation filtering has the effect of smoothing the phase transitions of the MSK signal even more. The output of the Gaussian filter then frequency modulates the carrier.</p>

<p>
  The instantaneous frequency deviation of a GMSK signal is proportional to the filtered data signal. If \( g(t) \) is the impulse response of the Gaussian filter and \( a_k \in \{-1, +1\} \) represents the input binary data, then the baseband signal \( u(t) \) after Gaussian filtering is:
</p>
        <div class="equation">
            $$u(t) = \sum_{k=-\infty}^{\infty} a_k g(t - kT)$$
        </div>
        <p>The GMSK signal \( s(t) \) is then given by:</p>
        <div class="equation">
            $$s(t) = \cos\left(2\pi f_c t + 2\pi f_d \int_{-\infty}^{t} u(\tau) d\tau + \phi_0\right)$$
        </div>
<p>
  where \( f_c \) is the carrier frequency, \( f_d \) is the frequency deviation constant, and \( \int_{-\infty}^{t} u(\tau) \, d\tau \) represents the phase integral of the filtered baseband signal. The parameter \( BT \) (bandwidth-time product) of the Gaussian filter is crucial in GMSK, controlling the trade-off between spectral efficiency and inter-symbol interference.
</p>
        <div class="note">
            <p>While GMSK offers superior spectral characteristics, the Gaussian filtering introduces inter-symbol interference (ISI). This ISI makes demodulation slightly more complex, often requiring more sophisticated equalization techniques at the receiver. Despite this, GMSK is widely used in applications like GSM (Global System for Mobile Communications) due to its excellent spectral efficiency and constant envelope property, which allows for the use of highly efficient, non-linear power amplifiers.</p>
        </div>