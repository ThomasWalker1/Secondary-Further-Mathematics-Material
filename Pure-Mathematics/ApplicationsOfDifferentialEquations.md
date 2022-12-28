In this section we discuss how we can model systems using differential equations.

# Simple Harmonic Motion

One type of system that we can model is a system that oscillates. If we just consider a system that has a purely sinusoidal behavior we can model it by the following:

$$\frac{d^2x}{dt^2}=-\omega^2x$$

Here $x$ represents the displacement of the object within our system from it's equilibrium position. The object is said to have simple harmonic motion. We can solve this to see that
$$x=A\sin(\omega t)+B\cos(\omega t) = R\sin(\omega t+\phi)$$
We fix the constant using the boundary conditions. The constant $R$ is referred to as the amplitude of the oscillation, and $\phi$ is the phase shift.

The differential equation we wrote above relates acceleration to displacement, but can we relate velocity to displacement?

To do this lets differentiate our expression for $x$
$$v=\frac{dx}{dt}=R\omega\cos(\omega t+\phi)=\sqrt{\omega^2R^2\cos(\omega t+\phi)}$$
$$=\sqrt{\omega^2R^2(1-\sin(\omega t+\phi))}=\sqrt{\omega^2(R^2-x^2)}\implies v^2=\omega^2(R^2-x^2)$$

# Damped Motion

In reality systems are not so simple, we have other factors that can affect an object's acceleration. Therefore, we now incorporate drag into our equations. Suppose the drag force on an object is given by
$$D=-\mathbf{K}v$$
Where here $v$ is velocity and $\mathbf{K}$ is a constant.
Adding this to our initial equation (using newton's second law, force=mass$\times$acceleration)
$$\frac{d^2x}{dt^2} = -\omega^2x-k\frac{dx}{dt}$$
$$\frac{d^2x}{dt^2}+k\frac{dx}{dt}+\omega^2x=0$$
Where $k=\frac{\mathbf{K}}{m}$

The resulting oscillations will now be damped as their is a force resisting it's motion. We can understand the nature of this damping by studying the solutions of the above equation. 

The above differential equation as auxillary equation, $\lambda^2+k\lambda+\omega^2=0$
- If $k^2-4\omega^2>0$ our solution is $x=Ae^{\alpha t}+Be^{\beta t}$, and we say the system is over-damped
- If $k^2-4\omega^2=0$ our solution is $x=(A+Bt)e^{-\frac{k}{2}t}$, and we say the system is critically damped
- If $k^2-4\omega^2<0$ our solution is $x=e^{-\frac{k}{2}t}(A\sin(qt)+B\cos(qt))$, and we say the system is under damped

# Coupled Differential Equations

Sometimes our system will contain interacting objects, so we now introduce the notion of coupled differential equations to try and model these.

The way we try to solve these is to eliminate one of the variables so that we can solve a differential equation in one variable instead. To do this it is often necessary to form a higher order differential equation. 

ADD EXAMPLE
