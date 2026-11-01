

# Vertical YouTube Shorts format
config.pixel_width = 1080
config.pixel_height = 1920
config.frame_width = 9
config.frame_height = 16

class NumeriqMaths(Scene):

    def construct(self):

        # Background
        self.camera.background_color = "#080D1B"

        # INTRO
        title = Text(
            "NUMERIQ",
            font_size=55,
            color=BLUE_B,
            weight=BOLD
        )

        tagline = Text(
            "MATHEMATICS BEYOND LIMITS",
            font_size=20,
            color=GOLD
        )

        intro = VGroup(title, tagline).arrange(DOWN, buff=0.3)

        self.play(FadeIn(intro, scale=0.8))
        self.wait(2)
        self.play(FadeOut(intro))

        # QUESTION
        heading = Text(
            "SOLVE THIS!",
            font_size=42,
            color=YELLOW
        ).to_edge(UP, buff=1)

        question = MathTex(
            r"\alpha =",
            r"\frac{1}{\sin60^\circ\sin61^\circ}",
            r"+\frac{1}{\sin62^\circ\sin63^\circ}",
            r"+\cdots",
            r"+\frac{1}{\sin118^\circ\sin119^\circ}",
            font_size=30
        )

        question.arrange(DOWN, buff=0.5)
        question.move_to(ORIGIN)

        self.play(Write(heading))
        self.play(Write(question))
        self.wait(3)

        self.play(
            FadeOut(question),
            FadeOut(heading)
        )

        # IDENTITY
        identity_title = Text(
            "IMPORTANT IDENTITY",
            font_size=36,
            color=YELLOW
        ).to_edge(UP, buff=1)

        identity = MathTex(
            r"\cot x-\cot y",
            r"=",
            r"\frac{\sin(y-x)}{\sin x\sin y}",
            font_size=40
        )

        identity.move_to(ORIGIN)

        self.play(Write(identity_title))
        self.play(Write(identity))
        self.wait(3)

        # SUBSTITUTE
        self.play(FadeOut(identity_title))
        self.play(identity.animate.scale(0.75).to_edge(UP))

        result = MathTex(
            r"\frac{1}{\sin x\sin(x+1^\circ)}",
            r"=",
            r"\frac{\cot x-\cot(x+1^\circ)}{\sin1^\circ}",
            font_size=30
        )

        result.move_to(ORIGIN)

        self.play(Write(result))
        self.wait(3)

        # APPLY TO QUESTION
        self.play(
            FadeOut(identity),
            FadeOut(result)
        )

        step_title = Text(
            "APPLY THE IDENTITY",
            font_size=38,
            color=YELLOW
        ).to_edge(UP, buff=1)

        expansion = MathTex(
            r"\alpha=\frac{1}{\sin1^\circ}\Big[",
            r"(\cot60^\circ-\cot61^\circ)",
            r"+(\cot62^\circ-\cot63^\circ)",
            r"+\cdots",
            r"+(\cot118^\circ-\cot119^\circ)",
            r"\Big]",
            font_size=27
        )

        expansion.arrange(DOWN, buff=0.45)
        expansion.move_to(ORIGIN)

        self.play(Write(step_title))
        self.play(Write(expansion))
        self.wait(4)

        # FINAL NOTE
        self.play(FadeOut(expansion))

        final_note = Text(
            "NOTICE THE PATTERN!",
            font_size=42,
            color=GREEN
        )

        explanation = Text(
            "The terms are grouped in pairs.\n"
            "Do not cancel across the gaps.",
            font_size=27,
            line_spacing=1.5
        )

        final_group = VGroup(
            final_note,
            explanation
        ).arrange(DOWN, buff=0.6)

        self.play(FadeIn(final_group))
        self.wait(4)

        # OUTRO
        self.play(FadeOut(final_group))
        outro = Text(
            "NUMERIQ",
            font_size=65,
            color=BLUE_B,
            weight=BOLD
        )

        self.play(Write(outro))
        self.wait(3)
