pico_simple_hardware_target(clocks)

pico_mirrored_target_link_libraries(hardware_clocks INTERFACE
        hardware_gpio
        hardware_irq
        hardware_resets
        hardware_pll
        # not currently used by clocks.c, but sensibly bundled here
        # as changing frequencies may require upping voltage
        hardware_vreg
        hardware_watchdog
        hardware_xosc
)

if (PICO_USE_FASTEST_SUPPORTED_CLOCK)
    target_compile_definitions(hardware_clocks INTERFACE PICO_USE_FASTEST_SUPPORTED_CLOCK=1)
endif()